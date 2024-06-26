import requests

def locate_phone(imei):
    url = f'https://api.example.com/locate/{imei}'  # Replace with actual API endpoint

    headers = {
        'Authorization': 'Bearer your_api_token_here',  # Replace with actual authorization token
        'Content-Type': 'application/json'
    }

    try:
        response = requests.get(url, headers=headers)
        if response.status_code == 200:
            location_data = response.json()
            latitude = location_data.get('latitude')
            longitude = location_data.get('longitude')
            accuracy = location_data.get('accuracy')
            timestamp = location_data.get('timestamp')

            print(f'Phone located successfully:')
            print(f'Latitude: {latitude}, Longitude: {longitude}, Accuracy: {accuracy} meters')
            print(f'Timestamp: {timestamp}')
        else:
            print(f'Failed to locate phone. Status code: {response.status_code}')
    except requests.exceptions.RequestException as e:
        print(f'Error locating phone: {e}')

# Example usage:
imei_number = '350593474556933'  # Replace with the IMEI number you want to locate
locate_phone(imei_number)
