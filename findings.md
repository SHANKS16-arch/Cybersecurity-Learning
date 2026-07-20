# Findings

## Scan Target
 
- Target: localhost (127.0.0.1)

## Open Ports

### Port 631

- Protocol: TCP
- Service: IPP(Internet Printing Protocol)
- Status: Open

##Observation

Out of the top 1000 common TCP ports scanned, only port 631 was open.

## Security Note
 Having fewer open ports reduces the attack surface of a system. However, every open service should be monitored and kept updated to avoid known vulnerablilities.

## Service Version 

- Service: CUPS
- Version: 2.4
- Why Version Detection Matters:

Knowing the software version helps security professionals determine whether the service has known vulnerabilities (CVEs). If vunlerabilities exist, softwaare should be updated or patched

## Vulnerability Research

 Service:
 CUPS 2.4

 Vulnerability:
 Some versions of CUPS have authentication bypass vulnerabilites. Whether a specific system is affected depends on its exact version, patches and configuration.

 Mitigation:
 - Update CUPS to the latest patched version.
 - Apply operating system security updates.
 - Restrict access using firewall or network configuration.
 - Disable the service if it is not requried.

## Recommendations

 - Keep CUPS updated with latest security patches.
 - Disable the printing service if it is not needed.
 - Regularly monitor open ports and running services.

## Operating System Detection

- Operating System: Linux (detected by Nmap)
- Why OS detection Matters:

Operating system detection helps security analysts to understand the target environment. Attackers  may search for OS-specific vulnerabilities,while defenders use this information to verify systems and ensure they are properly secured.


## Conclusion

 This project demonstrated how to perform basic network reconnassiance on a linux system using Nmap. The scan identified an open printingg sercive (CUPS), examined its version, and explored why service identification and vulnerability research are important in cybersecurit. This project also emphasized the importance of reducing the attack surface by disabling unnecessary services and keeping software updated.


## References

 1. Nmap Documentation (man nmap)
 2. OpenPrinting Cups Documentaion
 3. MITRE CVE Database
