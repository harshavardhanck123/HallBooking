# Hall Booking App

This is a simple hall booking application built using Express.js. It allows users to create rooms, book rooms, and retrieve booking information.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
  - [Create a Room](#create-a-room)
  - [Book a Room](#book-a-room)
  - [List All Rooms with Booked Data](#list-all-rooms-with-booked-data)
  - [List All Customers with Booked Data](#list-all-customers-with-booked-data)
  - [List Customer Booking Count](#list-customer-booking-count)
- [Contributing](#contributing)
- [License](#license)

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/yourusername/hall-booking-app.git
   cd hall-booking-app

2. Install the dependencies:
    ```bash
    npm install
3. Start the server:
    ```bash
    npm start

The server will be running on https://127.0.0.1/3001.

## Usage

The server will start on `http://127.0.0.1:3001`. You can use a tool like Postman or curl to interact with the API endpoints.

## API Endpoints
#### postman documentation
### Create a Room

- **URL:** `/rooms`
- **Method:** `POST`
- **Request Body:**
  ```json
  {
      "name": "Room A",
      "seats": 50,
      "amenities": ["Projector", "Wi-Fi"],
      "price": 100
  }
- **Response Body:**
```json
{
    "id": 1,
    "name": "Room A",
    "seats": 50,
    "amenities": ["Projector", "Wi-Fi"],
    "price": 100
}
```

### Book a Room   
- **URL:** `/bookings`
- **Method:** `POST`
- **Request Body:**
```json
{
          "customerName": "John Doe",
          "date": "2023-06-01",
          "startTime": "10:00",
          "endTime": "12:00",
          "roomId": 1
}
```
- **Response:**
```json

{
    "id": 1,
    "customerName": "John Doe",
    "date": "2023-06-01",
    "startTime": "10:00",
    "endTime": "12:00",
    "roomId": 1,
    "status": "Booked",
    "bookingDate": "2023-05-28T14:30:00.000Z"
}
```
### List All room with Booked Data  
- **URL:** `/rooms/bookings`
- **Method:** `GET`
- **Response**
```json
[
    {
        "name": "Room A",
        "bookedStatus": "Booked",
        "bookings": [
            {
                "id": 1,
                "customerName": "John Doe",
                "date": "2023-06-01",
                "startTime": "10:00",
                "endTime": "12:00",
                "roomId": 1,
                "status": "Booked"
            }
        ]
    }
]
```
### List All Customers with Booked Data  
- **URL:** `/customers/bookings`
- **Method:** `GET`
- **Response**
```json
{
    "customers": [
        {
            "name": "John Doe",
            "bookings": [
                {
                    "roomName": "Room A",
                    "date": "2023-06-01",
                    "startTime": "10:00",
                    "endTime": "12:00"
                }
            ]
        }
    ]
}
```

### List Customer Booking Count 
- **URL:** `/customers/:customerName/bookings/count`
- **Method:** `GET`
- **Response**
```json
{
    "customerName": "John Doe",
    "bookingCount": 1,
    "bookings": [
        {
            "customerName": "John Doe",
            "roomName": "Room A",
            "date": "2023-06-01",
            "startTime": "10:00",
            "endTime": "12:00",
            "bookingId": 1,
            "bookingDate": "2023-05-28T14:30:00.000Z",
            "bookingStatus": "Booked"
        }
    ]
}

```

### Contributing
Contributions are welcome! Please open an issue or submit a pull request.
