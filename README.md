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

<br>

## 📝 Collar (Use Cases)

- [ ] `Collar` sends GPS location data to the system. 

<br>

## 📝 Admin (Use Cases)

- [ ] `Admin` can ban (delete) `Tutor`

- [ ] `Admin` can register `Collar Tag ID`

<br>

- [ ] A `Person`who scans the QR Code on the `Collar` can view the `Pet`'s information and the `Tutor`'s contact details on theis device, as well as share their current location. 
