from flask import Flask, jsonify, request

app = Flask(__name__)

# Sample data storage (replace with your preferred database or ORM)
shipments = []

# API endpoint for creating a new shipment
@app.route('/shipments', methods=['POST'])
def create_shipment():
    data = request.get_json()
    shipments.append(data)
    return jsonify({'message': 'Shipment created successfully'})

# API endpoint for retrieving all shipments
@app.route('/shipments', methods=['GET'])
def get_all_shipments():
    return jsonify(shipments)

# API endpoint for retrieving a specific shipment
@app.route('/shipments/<int:shipment_id>', methods=['GET'])
def get_shipment(shipment_id):
    for shipment in shipments:
        if shipment['id'] == shipment_id:
            return jsonify(shipment)
    return jsonify({'message': 'Shipment not found'})

# API endpoint for updating a shipment
@app.route('/shipments/<int:shipment_id>', methods=['PUT'])
def update_shipment(shipment_id):
    data = request.get_json()
    for shipment in shipments:
        if shipment['id'] == shipment_id:
            shipment.update(data)
            return jsonify({'message': 'Shipment updated successfully'})
    return jsonify({'message': 'Shipment not found'})

# API endpoint for deleting a shipment
@app.route('/shipments/<int:shipment_id>', methods=['DELETE'])
def delete_shipment(shipment_id):
    for shipment in shipments:
        if shipment['id'] == shipment_id:
            shipments.remove(shipment)
            return jsonify({'message': 'Shipment deleted successfully'})
    return jsonify({'message': 'Shipment not found'})

if __name__ == '__main__':
    app.run()
