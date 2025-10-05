

import 'package:flutter/material.dart';
void main() => runApp(MaterialApp(home: LoginPage(), debugShowCheckedModeBanner: false));
class LoginPage extends StatelessWidget {
  final emailCtrl = TextEditingController();
  final passCtrl = TextEditingController();
  void login(BuildContext ctx) {
    final e = emailCtrl.text.trim(), p = passCtrl.text;
    final valid = e == '24mit031@hicas.ac.in' && p == 'Lotus@031';
    ScaffoldMessenger.of(ctx).showSnackBar(
      SnackBar(content: Text(valid ? 'Login Success' : 'Invalid Login')));
    if (valid) Navigator.push(ctx, MaterialPageRoute(builder: (_) => Welcome()));
  }
  @override
  Widget build(BuildContext c) => Scaffold(
    appBar: AppBar(title: Text('Student Login')),
    body: Padding(
      padding: EdgeInsets.all(20),
      child: Column(mainAxisAlignment: MainAxisAlignment.center, children: [
        TextField(controller: emailCtrl, decoration: InputDecoration(labelText: 'Email')),
        TextField(controller: passCtrl, decoration: InputDecoration(labelText: 'Password'), obscureText: true),
        SizedBox(height: 20),
        ElevatedButton(onPressed: () => login(c), child: Text('Login'))
      ]),
    ),
  );
}
class Welcome extends StatelessWidget {
  @override
  Widget build(BuildContext c) => Scaffold(
    appBar: AppBar(title: Text('Welcome')),
    body: Center(child: Text('Welcome Guys..!!!', style: TextStyle(fontSize: 24))),
  );
}

