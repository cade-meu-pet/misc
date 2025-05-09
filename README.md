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
![cade-meu-pet-uml drawio(2)](https://github.com/user-attachments/assets/3a227198-a2b9-4927-982e-44a86eb3f529)




## Architecture Diagram
![cade-meu-pet-architecture drawio(3)](https://github.com/user-attachments/assets/6abaf01f-1d8a-4d61-826e-a411b25393ee)




