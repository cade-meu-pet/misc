# 🗃️ Misc

Para assuntos diversos do projeto cade-meu-pet

<br>

# 🐾 (UML-Like) Use Case

> Diagrama de Casos de Uso do Cade-Meu-Pet

<br>

## 🎭 Actors

- Tutor

- Collar

- Admin

- Person

<br>

## 📝 Tutor (Use Cases)

- [ ] `Tutor` can signup. 

- [ ] `Tutor` can signin (authenticate).

- [ ] Authenticated `Tutor` can register `Pet` only if they have `Collar Tag ID`

- [ ] Authenticated `Tutor` can update/delete `Pet` register.

- [ ] Authenticated `Tutor` can view update/delete account

- [ ] Auhtenticated `Tutor` can view pets information
- [ ] Authenticated `Tutor` can enable/disable `Collar` routine

<br>

## 📝 Collar (Use Cases)

- [ ] `Collar` sends GPS location data to the system when enable.
- [ ] `Collar` has a QR code linking to the tutor's and pet's contact information page.
 
<br>

## 📝 Admin (Use Cases)

- [ ] `Admin` can ban (delete) `Tutor`

- [ ] `Admin` can register `Collar` Tag ID

- [ ] `Admin` can register Colar QrCode

<br>

- [ ] A `Person`who scans the QR Code on the `Collar` can view the `Pet`'s information and the `Tutor`'s contact details on theis device, as well as share their current location. 


## Use Cases Diagram: 
![image](https://github.com/user-attachments/assets/5bdd4111-f8c3-430e-a8e2-b3536b323671)

## Architecture Diagram
![image](https://github.com/user-attachments/assets/70c9fda6-c987-4b64-83f8-b04db726c111)


