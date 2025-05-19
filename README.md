# 🗃️ Misc
Para assuntos diversos do projeto cade-meu-pet

<br>

![image](https://github.com/user-attachments/assets/16c089ec-41dd-4199-a4dc-c35dc56a694c)

<br>

# 🐾 (UML-Like) Use Case

> Diagrama de Casos de Uso do Cade-Meu-Pet

<br>

## 🎭 Actors

- Tutor

- ~Collar~

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
- [ ] ~Authenticated `Tutor` can enable/disable `Collar` routine~

<br>

## ~📝 Collar (Use Cases)~

- [ ] ~`Collar` sends GPS location data to the system when enable.~
- [ ] ~`Collar` has a QR code linking to the tutor's and pet's contact information page.~
 
<br>

## 📝 Admin (Use Cases)

- [ ] `Admin` can ban (delete) `Tutor`

- [ ] `Admin` can register `Collar` Tag ID

- [ ] `Admin` can register Colar QrCode

<br>

- [ ] A `Person`who scans the QR Code on the `Collar` can view the `Pet`'s information and the `Tutor`'s contact details on theis device, as well as share their current location. 


## Use Cases Diagram: 
<br>
<br>

![cade-meu-pet-uml drawio](https://github.com/user-attachments/assets/8aa446dd-c1f4-420f-8e68-4a373093ab4a)

<br>
<br>

## Architecture Diagram
![cade-meu-pet-architecture drawio(3)](https://github.com/user-attachments/assets/6abaf01f-1d8a-4d61-826e-a411b25393ee)

<br>
<br>

## Database Design
![image](https://github.com/user-attachments/assets/2d642190-6e5a-479e-82d6-d2315b7e086c)




