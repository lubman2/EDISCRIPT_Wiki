# XML Schéma pro COMDIS Konverzi
## Vizuální Struktura

```
COMDIS (root)
│
├── Header
│   ├── Interchange
│   │   ├── SyntaxVersion        : "UNOD:3"
│   │   ├── Sender               : "8594195490002:14"
│   │   ├── Receiver             : "8595149000001:14"
│   │   ├── InterchangeDate      : "251113"
│   │   ├── InterchangeTime      : "2013"
│   │   └── InterchangeControlRef: "590880426"
│   │
│   ├── Message
│   │   ├── MessageType          : "COMDIS"
│   │   ├── Version              : "D"
│   │   ├── Release              : "01B"
│   │   └── MessageRefNumber     : "530266478"
│   │
│   ├── MessageMetadata
│   │   ├── TestIndicator        : "94W" (T=Test, P=Prod)
│   │   ├── RepeatingGroupNumber : "1"
│   │   └── InterchangeControlType: "2"
│   │
│   └── DocumentInfo
│       ├── DocumentType         : "67" (Code for COMDIS)
│       ├── DocumentNumber       : "FP703632526"
│       ├── DocumentStatus       : "9"
│       └── CreationDate         : "20251113"
│
├── Parties
│   ├── Buyer
│   │   ├── GLN                  : "8594195490002"
│   │   └── Name                 : "Smarty CZ a.s."
│   │
│   └── Supplier
│       ├── GLN                  : "8595149000001"
│       └── Name                 : "AT Computers a.s."
│
├── ForecastPeriods  (1..n periods)
│   │
│   ├── Period [0]
│   │   ├── PeriodNumber         : "01643674"
│   │   ├── StartDate            : "20251113"
│   │   │
│   │   └── Items  (1..n items)
│   │       │
│   │       ├── Item [0]
│   │       │   ├── LineItemNumber   : "1"
│   │       │   ├── ProductNumber    : "PROD001"
│   │       │   ├── ProductDesc      : "Laptop Model X1"
│   │       │   ├── Quantity         : "100"
│   │       │   ├── Unit             : "PCE"
│   │       │   └── DeliveryDate     : "20251120"
│   │       │
│   │       └── Item [1]
│   │           ├── LineItemNumber   : "2"
│   │           ├── ProductNumber    : "PROD002"
│   │           ├── ProductDesc      : "Mouse Wireless"
│   │           ├── Quantity         : "500"
│   │           ├── Unit             : "PCE"
│   │           └── DeliveryDate     : "20251120"
│   │
│   └── Period [1]  ... (další periody)
│
└── Control
    ├── SegmentCount            : "14"
    ├── GroupCount              : "1"
    └── MessageControlCount     : "1"
```

---

## 📋 XSD Definice (XML Schema)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  
  <xs:element name="COMDIS" type="ComdisType"/>
  
  <xs:complexType name="ComdisType">
    <xs:sequence>
      <xs:element name="Header" type="HeaderType"/>
      <xs:element name="Parties" type="PartiesType"/>
      <xs:element name="ForecastPeriods" type="ForecastPeriodsType"/>
      <xs:element name="Control" type="ControlType"/>
    </xs:sequence>
  </xs:complexType>
  
  <xs:complexType name="HeaderType">
    <xs:sequence>
      <xs:element name="Interchange" type="InterchangeType"/>
      <xs:element name="Message" type="MessageType"/>
      <xs:element name="MessageMetadata" type="MessageMetadataType"/>
      <xs:element name="DocumentInfo" type="DocumentInfoType"/>
    </xs:sequence>
  </xs:complexType>
  
  <xs:complexType name="InterchangeType">
    <xs:sequence>
      <xs:element name="SyntaxVersion" type="xs:string"/>
      <xs:element name="Sender" type="xs:string"/>
      <xs:element name="Receiver" type="xs:string"/>
      <xs:element name="InterchangeDate" type="xs:string"/>
      <xs:element name="InterchangeTime" type="xs:string"/>
      <xs:element name="InterchangeControlReference" type="xs:string"/>
    </xs:sequence>
  </xs:complexType>
  
  <xs:complexType name="MessageType">
    <xs:sequence>
      <xs:element name="MessageType" type="xs:string"/>
      <xs:element name="Version" type="xs:string"/>
      <xs:element name="Release" type="xs:string"/>
      <xs:element name="MessageReferenceNumber" type="xs:string"/>
    </xs:sequence>
  </xs:complexType>
  
  <xs:complexType name="MessageMetadataType">
    <xs:sequence>
      <xs:element name="TestIndicator" type="xs:string"/>
      <xs:element name="RepeatingGroupNumber" type="xs:integer"/>
      <xs:element name="InterchangeControlType" type="xs:integer"/>
    </xs:sequence>
  </xs:complexType>
  
  <xs:complexType name="DocumentInfoType">
    <xs:sequence>
      <xs:element name="DocumentType" type="xs:string"/>
      <xs:element name="DocumentNumber" type="xs:string"/>
      <xs:element name="DocumentStatus" type="xs:string"/>
      <xs:element name="CreationDate" type="xs:string"/>
    </xs:sequence>
  </xs:complexType>
  
  <xs:complexType name="PartiesType">
    <xs:sequence>
      <xs:element name="Buyer" type="PartyType"/>
      <xs:element name="Supplier" type="PartyType"/>
    </xs:sequence>
  </xs:complexType>
  
  <xs:complexType name="PartyType">
    <xs:sequence>
      <xs:element name="GLN" type="xs:string"/>
      <xs:element name="Name" type="xs:string"/>
    </xs:sequence>
  </xs:complexType>
  
  <xs:complexType name="ForecastPeriodsType">
    <xs:sequence>
      <xs:element name="Period" type="PeriodType" maxOccurs="unbounded"/>
    </xs:sequence>
  </xs:complexType>
  
  <xs:complexType name="PeriodType">
    <xs:sequence>
      <xs:element name="PeriodNumber" type="xs:string"/>
      <xs:element name="StartDate" type="xs:string"/>
      <xs:element name="Items" type="ItemsType"/>
    </xs:sequence>
    <xs:attribute name="index" type="xs:integer"/>
  </xs:complexType>
  
  <xs:complexType name="ItemsType">
    <xs:sequence>
      <xs:element name="Item" type="ItemType" maxOccurs="unbounded"/>
    </xs:sequence>
  </xs:complexType>
  
  <xs:complexType name="ItemType">
    <xs:sequence>
      <xs:element name="LineItemNumber" type="xs:string"/>
      <xs:element name="ProductNumber" type="xs:string"/>
      <xs:element name="ProductDescription" type="xs:string" minOccurs="0"/>
      <xs:element name="Quantity" type="xs:decimal"/>
      <xs:element name="Unit" type="xs:string"/>
      <xs:element name="DeliveryDate" type="xs:string" minOccurs="0"/>
    </xs:sequence>
    <xs:attribute name="index" type="xs:integer"/>
  </xs:complexType>
  
  <xs:complexType name="ControlType">
    <xs:sequence>
      <xs:element name="SegmentCount" type="xs:integer"/>
      <xs:element name="GroupCount" type="xs:integer"/>
      <xs:element name="MessageControlCount" type="xs:integer"/>
    </xs:sequence>
  </xs:complexType>
  
</xs:schema>
```

---

## 🔄 Transformační Tok

```
EDIFACT COMDIS Input
        │
        │ [EDIREAD]
        ↓
    EDIFACT Parser (@0 object)
        │
        │ [EDIGET na segmenty]
        ├─→ UNB, UNH, USH
        ├─→ BGM, DTM
        ├─→ NAD (Parties)
        ├─→ USC (Periods)
        ├─→ LIN, IMD, QTY (Items)
        └─→ UNZ, CNT (Control)
        │
        │ [XMLTAG, XMLTEXTSET]
        ↓
    XML Builder (@0 object)
        │
        │ [XMLSAVE]
        ↓
    XML Output File
```

---

## 💾 Příklad Výstupního XML

```xml
<?xml version="1.0" encoding="UTF-8"?>
<COMDIS>
  <Header>
    <Interchange>
      <SyntaxVersion>UNOD:3</SyntaxVersion>
      <Sender>8594195490002:14</Sender>
      <Receiver>8595149000001:14</Receiver>
      <InterchangeDate>251113</InterchangeDate>
      <InterchangeTime>2013</InterchangeTime>
      <InterchangeControlReference>590880426</InterchangeControlReference>
    </Interchange>
    <Message>
      <MessageType>COMDIS</MessageType>
      <Version>D</Version>
      <Release>01B</Release>
      <MessageReferenceNumber>530266478</MessageReferenceNumber>
    </Message>
    <MessageMetadata>
      <TestIndicator>94W</TestIndicator>
      <RepeatingGroupNumber>1</RepeatingGroupNumber>
      <InterchangeControlType>2</InterchangeControlType>
    </MessageMetadata>
    <DocumentInfo>
      <DocumentType>67</DocumentType>
      <DocumentNumber>FP703632526</DocumentNumber>
      <DocumentStatus>9</DocumentStatus>
      <CreationDate>20251113</CreationDate>
    </DocumentInfo>
  </Header>
  <Parties>
    <Buyer>
      <GLN>8594195490002</GLN>
      <Name>Smarty CZ a.s.</Name>
    </Buyer>
    <Supplier>
      <GLN>8595149000001</GLN>
      <Name>AT Computers a.s.</Name>
    </Supplier>
  </Parties>
  <ForecastPeriods>
    <Period index="0">
      <PeriodNumber>01643674</PeriodNumber>
      <StartDate>20251113</StartDate>
      <Items>
        <Item index="0">
          <LineItemNumber>1</LineItemNumber>
          <ProductNumber>PROD001</ProductNumber>
          <ProductDescription>Laptop Model X1</ProductDescription>
          <Quantity>100.00</Quantity>
          <Unit>PCE</Unit>
          <DeliveryDate>20251120</DeliveryDate>
        </Item>
      </Items>
    </Period>
  </ForecastPeriods>
  <Control>
    <SegmentCount>14</SegmentCount>
    <GroupCount>1</GroupCount>
    <MessageControlCount>1</MessageControlCount>
  </Control>
</COMDIS>
```

---

## 🎯 EDIFACT → XML Mapování Příklady

### Příklad 1: Sender Information
**EDIFACT:** `UNB+UNOD:3+8594195490002:14+...`
```xml
<Interchange>
  <SyntaxVersion>UNOD:3</SyntaxVersion>
  <Sender>8594195490002:14</Sender>
  ...
</Interchange>
```

### Příklad 2: Party Information
**EDIFACT:**
```
NAD+BY+8594195490002::9++Smarty CZ a.s.'
NAD+SU+8595149000001::9++AT Computers a.s.'
```
```xml
<Parties>
  <Buyer>
    <GLN>8594195490002</GLN>
    <Name>Smarty CZ a.s.</Name>
  </Buyer>
  <Supplier>
    <GLN>8595149000001</GLN>
    <Name>AT Computers a.s.</Name>
  </Supplier>
</Parties>
```

### Příklad 3: Forecast Items
**EDIFACT:**
```
USC+01643674+++++2+4'
LIN+1+PROD001+++...'
IMD+...+Laptop Model X1'
QTY+1:100:PCE'
DTM+2:20251120'
```
```xml
<Period index="0">
  <PeriodNumber>01643674</PeriodNumber>
  <Items>
    <Item index="0">
      <LineItemNumber>1</LineItemNumber>
      <ProductNumber>PROD001</ProductNumber>
      <ProductDescription>Laptop Model X1</ProductDescription>
      <Quantity>100</Quantity>
      <Unit>PCE</Unit>
      <DeliveryDate>20251120</DeliveryDate>
    </Item>
  </Items>
</Period>
```

---

## 🚦 Status Kódy v COMDIS

| BGM Kód | Popis |
|---------|-------|
| 67 | Original |
| 68 | Replacement |
| 69 | Cancellation |

| Indicator | Popis |
|-----------|-------|
| 9 | Production/Test Data (94W) |
| 1 (USH) | Test |
| 2 | Production |

---

## 📈 Kapacita Smyček

Script je navržen pro:
- **Periody (USC):** 1-999
- **Položky (LIN) per periodu:** 1-999
- **Segmenty:** bez limitu (dynamické čtení)

