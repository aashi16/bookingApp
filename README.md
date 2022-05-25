
## Hotel Application

A Vue application that manages the process of booking a hotel room.

<img width="1400" alt="Desktop" src="https://user-images.githubusercontent.com/83874139/170195284-3b2d4fe9-5873-4554-a557-b8ed8ad5ba76.png">
<img width="349" alt="mobileApp" src="https://user-images.githubusercontent.com/83874139/170195312-989a97fa-6da4-4127-9d44-5767faf953a3.png">

## Features

- Responsive app
- Location Can be searched by pincode, address, city etc.
- Room Selection calculated based on the count of Adult.
- Range calendar.
- Save the selected search filters in local storage
- Update reservation summary to json

## Tech Stack

- vue
- axios
- vue2-datepicker
- vue-place-autocomplete
- bootstrap

## Run Locally

Install dependencies

```bash
  npm install
```

Install JSON Server

```bash
npm install -g json-server
```

To Start JSON serve

```bash
json-server --watch db.json
```

Now go to http://localhost:3000/bookings, to check data

To Start Server

```bash
  npm run serve
```
