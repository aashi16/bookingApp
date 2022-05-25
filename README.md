## Hotel Application

A Vue application that manages the process of booking a hotel room.

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
