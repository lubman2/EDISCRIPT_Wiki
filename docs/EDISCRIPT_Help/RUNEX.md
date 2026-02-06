EDI Script - (c) EDICOM s.r.o.

# RUNEX

is an instruction for running a program on an externel PC. The script can wait till
        the program is finished. The flag is set on if an instruction is not successful.
        The instruction is based on distributed COM technologi. A user have to register
        EDICOM RunEx component using command line:

**RunEx /Regserver**

        The user can check if component is registered succesfuly by using program dcomcnfg.exe.
        If DCOM is not instaled on a PC run dcom98.exe and dcm98cfg.exe. Settings for DCOM
        (dcomcnfg.exe) should be:

        Autentication Level = None

        Default Impersonation Level = Identify

        If the instruction works only once (usualy in Windows 95) then run program EdiLoader.exe.
        The program will keep komponent in memory till you stop the program. The instruction
        has no problem to use this component then.

        The component is possible to unregister using command line:

**RunEx /Unregserver**

### Format:

## RUNEX exe pc x

exe command line pc name of PC where to run program x 0 = not wait for end of program; 1 = wait for end of program

### Example:

RUNEX "myprog.exe" "N366" 1

        RUNEX "myprog.exe" "169.254.255.2" 1

### See also:

[PROGPATH](PROGPATH.md)

[RUN](RUN.md)

[RUNS](RUNS.md)

[RUNX](RUNX.md)
