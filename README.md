---

# Advanced Exchanger

Advanced Exchanger is a Flutter application that provides real-time currency conversion. The app allows users to input an amount in a base currency and dynamically convert it to multiple other currencies.

## Table of Contents

- [Features](#features)
- [Architecture](#architecture)
- [Setup](#setup)
- [Running the App](#running-the-app)
- [API Usage](#api-usage)
- [Database](#database)
- [Error Handling](#error-handling)
- [Dependencies](#dependencies)

## Features

- Real-time currency conversion
- Persistent storage of selected currencies using SQLite
- Dynamic UI updates as the user inputs the base amount
- Supports multiple conversions at once
- Handles network errors gracefully with retry options

## Architecture

The application follows the MVVM (Model-View-ViewModel) architecture pattern, which is particularly well-suited for Flutter applications as it separates the business logic from the UI. Here's a brief explanation of the main components:

- **Model**: Represents the data and business logic of the app. This includes classes like `CurrencyCardModel` and the `SqlDatabaseService` for database operations.
- **View**: The UI components of the app, including widgets and screens like `HomePage` and `CurrencyCardWidget`.
- **ViewModel (Store)**: Manages the data flow between the model and the view. We used the MobX package to create stores like `CurrencyStore` which handle state management and business logic.

## Setup

### Prerequisites

- Flutter SDK: [Install Flutter](https://flutter.dev/docs/get-started/install)
- Dart SDK: Comes with Flutter installation
- An API key from [apilayer](https://apilayer.com/marketplace/exchangerates_data-api) 

### Installation

1. **Unzip the project**:

   Download the zipped project and unzip it to your desired directory.

2. **Navigate to the project directory**:

   ```bash
   cd path_to_unzipped_project
   ```

3. **Install dependencies**:

   ```bash
   flutter pub get
   ```

4. **Generate MobX code**:

   ```bash
   flutter packages pub run build_runner build --delete-conflicting-outputs
   ```

5. **Set up environment variables**:

   Find a `.env` file in the root directory and add your API key:

   ```
   API_BASE_URL=https://api.apilayer.com/
   API_KEY=your_api_key_here
   ```

## Running the App

1. **Run the app**:

   ```bash
   flutter run
   ```

2. **Build the app for release**:

   ```bash
   flutter build apk --release
   ```

## API Usage

The app uses the apilayer Exchange Rates Data API to fetch real-time exchange rates. Here are the key API endpoints used:

- `GET /exchangerates_data/symbols`: Fetches available currency symbols.
- `GET /exchangerates_data/latest`: Fetches the latest exchange rates for given symbols.
- `GET /exchangerates_data/convert`: Converts an amount from one currency to another.

## Database

The app uses SQLite for local data persistence. The `SqlDatabaseService` class handles database creation, reading, writing, and deleting operations.

### Database Schema

- **currency_cards**:
  - `id`: INTEGER PRIMARY KEY AUTOINCREMENT
  - `currencyCode`: TEXT
  - `currencyName`: TEXT
  - `flagIcon`: TEXT

## Error Handling

The app handles various errors, including network errors and API limits, by displaying appropriate messages using custom snack bars. A retry option is provided for network-related errors.

## Dependencies

- `flutter_mobx`: State management
- `mobx`: State management
- `sqflite`: SQLite database
- `path`: For handling file paths
- `loading_animation_widget`: Loading animations
- `flutter_dotenv`: Environment variables
- `get_it`: Service locator
- `responsive_sizer`: Responsive design
- `flutter_svg`: SVG rendering
- `lottie`: For animations
- `permission_handler`: To handle app permissions
- `go_router`: For navigation
- `shared_preferences`: For storing preferences

---
