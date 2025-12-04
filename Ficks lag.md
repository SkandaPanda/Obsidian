# Ficks lagar (Diffusion)

**Ficks lagar** beskriver diffusion, det vill säga hur partiklar (atomer, molekyler) rör sig från områden med hög koncentration till områden med låg koncentration.

---

## Ficks första lag
Denna lag används vid **stationära förhållanden** (steady state), där koncentrationen inte ändras med tiden. Den säger att flödet är proportionellt mot koncentrationsgradienten.

$$
J = -D \frac{dC}{dx}
$$

**Där:**
* $J = \text{Diffusionsflöde} \quad [\frac{\text{mol}}{m^2 \cdot s}]$
* $D = \text{Diffusionskoefficient} \quad [\frac{m^2}{s}]$
* $C = \text{Koncentration} \quad [\frac{\text{mol}}{m^3}]$
* $x = \text{Position} \quad [m]$
* $\frac{dC}{dx} = \text{Koncentrationsgradient}$

> [!NOTE] Minustecknet
> Minustecknet i ekvationen indikerar att diffusionen sker i *motsatt* riktning mot gradienten – alltså från hög koncentration till låg koncentration.

---

## Ficks andra lag
Denna lag beskriver **icke-stationära förhållanden** (non-steady state), det vill säga hur koncentrationen på en viss plats förändras med tiden.

$$
\frac{\partial C}{\partial t} = D \frac{\partial^2 C}{\partial x^2}
$$

**Beskrivning:**
* $\frac{\partial C}{\partial t}$ beskriver hur snabbt koncentrationen ändras i en specifik punkt.
* Den visar att förändringshastigheten är proportionell mot hur "krökt" koncentrationsprofilen är (derivatan av gradienten).

---

### Sammanfattning
| Lag | Användning | Ekvation |
| :--- | :--- | :--- |
| **Första** | Stationärt flöde (konstant flöde) | $J = -D \nabla C$ |
| **Andra** | Tidsberoende förändring | $\frac{\partial C}{\partial t} = D \nabla^2 C$ |