# Nessus Finding: SSL Certificate Cannot Be Trusted (Plugin 51192)

## Summary
- **Tool:** Tenable Nessus Essentials
- **Scan Template:** Basic Network Scan
- **Target:** 127.0.0.1
- **Service/Port:** 8834/tcp (www)
- **Finding:** SSL Certificate Cannot Be Trusted
- **Severity:** Medium
- **CVSS v3.0 Base Score:** 6.5
- **Plugin ID:** 51192

## Evidence (Nessus Plugin Output)
Nessus reported that the certificate at the top of the chain sent by the remote host is signed by an unknown certificate authority.

- **Subject:** `O=Nessus Users United / OU=Nessus Server / L=New York / C=US / ST=NY / CN=MacBookPro.lan`
- **Issuer:** `O=Nessus Users United / OU=Nessus Certification Authority / L=New York / C=US / ST=NY / CN=Nessus Certification Authority`
- **Observed on:** `127.0.0.1:8834`

## Impact
A certificate that cannot be validated to a trusted CA prevents reliable verification of server identity.  
If this service is exposed beyond localhost or an internal admin network, it can increase the risk of man-in-the-middle (MITM) attacks and user trust failures.

## Remediation
- Keep Nessus UI access restricted (avoid exposing/port-forwarding **8834/tcp**).
- If remote access is required, replace the default certificate with one signed by a trusted internal PKI or public CA and implement certificate rotation/renewal.

## Retest Plan
- Re-run the scan after remediation.
- Confirm Plugin **51192** no longer appears for the affected host/port.
