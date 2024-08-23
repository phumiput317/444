import 'dart:convert';
import 'package:http/http.dart' as http;

class Product {
  final String title;
  final double price;
  final String image;
  final String category;
  final String description;
  final double rating;
  final int count;

  Product({
    required this.title,
    required this.price,
    required this.image,
    required this.category,
    required this.description,
    required this.rating,
    required this.count,
  });

  factory Product.fromJson(Map<String, dynamic> json) {
    return Product(
      title: json['title'],
      price: json['price'].toDouble(),
      image: json['image'],
      category: json['category'],
      description: json['description'],
      rating: json['rating']['rate'].toDouble(),
      count: json['rating']['count'],
    );
  }
}

Future<List<Product>> fetchProducts() async {
  final response = await http.get(Uri.parse('https://fakestoreapi.com/products'));

  if (response.statusCode == 200) {
    List jsonResponse = json.decode(response.body);
    return jsonResponse.map((product) => Product.fromJson(product)).toList();
  } else {
    throw Exception('Failed to load products');
  }
}
