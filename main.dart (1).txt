// ignore_for_file: deprecated_member_use

import 'package:clone/card.dart';
import 'package:clone/location.dart';
import 'package:clone/splash_screen.dart';
import 'package:clone/whatsapp.dart';
import 'package:flutter/material.dart';
import 'package:flutter_phone_direct_caller/flutter_phone_direct_caller.dart';
import 'package:font_awesome_flutter/font_awesome_flutter.dart';
import 'package:url_launcher/url_launcher.dart';

void main() {
  runApp(const MaterialApp(
    debugShowCheckedModeBanner: false,
    home: SplashScreen(title: '',),
  ));
}

class MyApp extends StatefulWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  State<MyApp> createState() => _MyAppState();
}

class _MyAppState extends State<MyApp> {
  final Uri webLink = Uri.parse('https://www.jayanathanchits.com/');
  final Uri instLink = Uri.parse(
      'https://instagram.com/sreejayanathanchits?igshid=MWZjMTM2ODFkZg==');
  final Uri facebookLink = Uri.parse('https://m.facebook.com/SjChits');
  final Uri youtubeLink = Uri.parse(
      'https://youtube.com/@sreejayanathanchits6684?si=R6RLsoKlhSYesqQa');

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        backgroundColor: Colors.white,
        body: SafeArea(
          child: Expanded(
            child: Column(
              children: <Widget>[
                const SizedBox(
                  height: 20,
                ),
                const Image(image: AssetImage('assets/img/logo.jpg')),
                const SizedBox(
                  height: 12,
                ),
          
                // Cards
          
                GestureDetector(
                  onTap: () {
                    cardPopUp1();
                  },
                  child: const Image(
                      width: 350, image: AssetImage('assets/img/card1.jpeg')),
                ),
                const SizedBox(
                  height: 15,
                ),
                GestureDetector(
                  onTap: () => cardPopUp2(),
                  child: const Image(
                      width: 350, image: AssetImage('assets/img/card2.jpeg')),
                ),
                const SizedBox(
                  height: 200,
                ),
          
                // bottom Social media Icon and popup
          
                // const SizedBox(
                //   height: 20,
                // ),
          
                Row(
                  mainAxisAlignment: MainAxisAlignment.spaceAround,
                  children: [
                    const Padding(
                        padding: EdgeInsets.only(bottom: 130, left: 15)),
                    IconButton(
                      onPressed: () {
                        launchUrl(webLink);
                      },
                      icon: const Icon(Icons.language),
                      iconSize: 40,
                      color: Colors.black,
                    ),
                    GestureDetector(
                        onTap: () {
                          launchUrl(instLink);
                        },
                        child: const Image(
                            height: 32,
                            image: AssetImage('assets/img/instagram.png'))),
                    IconButton(
                        onPressed: () {
                          launchUrl(facebookLink);
                        },
                        icon: const Icon(
                          FontAwesomeIcons.facebookSquare,
                          color: Color.fromARGB(255, 37, 90, 134),
                          size: 35,
                        )),
                    GestureDetector(
                        onTap: () {
                          launchUrl(youtubeLink);
                        },
                        child: const Image(
                            height: 35,
                            image: AssetImage('assets/img/youtube.png'))),
                    const SizedBox(
                      width: 45,
                    ),
                    IconButton(
                        onPressed: () => callPopup(),
                        icon: const Icon(
                          Icons.phone_in_talk,
                          size: 35,
                          color: Colors.blue,
                        )),
                    GestureDetector(
                        onTap: () => whatsappPop(),
                        child: const Image(
                            height: 32,
                            image: AssetImage('assets/img/whatsapp.png'))),
                    IconButton(
                        onPressed: () => locationPopup(),
                        icon: const Icon(
                          Icons.location_on,
                          size: 38,
                          color: Colors.red,
                        )),
                  ],
                ),
              ],
            ),
          ),
        ),
        bottomNavigationBar: Container(
          color: Colors.white,
          child: const Row(
            mainAxisAlignment: MainAxisAlignment.end,
            children: [
              Padding(
                padding: EdgeInsets.only(bottom: 15, right: 15),
                child: SizedBox(
                  // padding: EdgeInsets.fromLTRB(100, 0, 0, 0),
                  // color: Colors.white,
                  height: 25,
                  child: Text(
                    'Toll Free : 1800 425 1432  ',
                    style: TextStyle(
                        color: Color.fromARGB(255, 33, 32, 32),
                        fontSize: 18.0,
                        fontWeight: FontWeight.bold),
                  ),
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }

  Future cardPopUp1() {
    return showDialog(
      context: context,
      builder: (context) {
        return AlertDialog(
          title: Container(
            alignment: Alignment.topCenter,
            child: const Image(
                height: 150, image: AssetImage('assets/img/logoPop.png')),
          ),
          actions: [
            SizedBox(
              width: 400,
              height: 150,
              child: Column(
                children: [
                  const Center(
                    child: Text(
                      "Announcement",
                      style:
                          TextStyle(fontWeight: FontWeight.bold, fontSize: 15),
                    ),
                  ),
                  const Center(
                    child: Text(
                      "New scheme Started on December",
                      style: TextStyle(fontSize: 14),
                    ),
                  ),
                  const Center(
                    child: Text("2021", style: TextStyle(fontSize: 14)),
                  ),
                  const SizedBox(
                    height: 10,
                  ),
                  Row(
                    mainAxisAlignment: MainAxisAlignment.end,
                    children: [
                      Container(
                        padding: const EdgeInsets.only(right: 15),
                        child: TextButton(
                          child: const Text(
                            'Close',
                            style:
                                TextStyle(fontSize: 18, color: Colors.black87),
                          ),
                          onPressed: () {
                            Navigator.of(context).pop();
                          },
                        ),
                      ),
                      Container(
                        padding: const EdgeInsets.only(right: 15),
                        child: TextButton(
                          child: const Text(
                            'Yes',
                            style:
                                TextStyle(fontSize: 18, color: Colors.black87),
                          ),
                          onPressed: () {
                            Navigator.of(context).push(
                              MaterialPageRoute(
                                builder: (BuildContext context) {
                                  return const CardOneImage();
                                },
                              ),
                            );
                          },
                        ),
                      ),
                    ],
                  ),
                ],
              ),
            )
          ],
        );
      },
    );
  }

  Future cardPopUp2() {
    return showDialog(
      context: context,
      builder: (context) {
        return AlertDialog(
          title: Container(
            alignment: Alignment.topCenter,
            child: const Image(
                height: 180, image: AssetImage('assets/img/logoPop.png')),
          ),
          actions: [
            SizedBox(
              width: 300,
              height: 200,
              child: Column(
                children: [
                  const Center(
                    child: Text(
                      "Announcement",
                      style:
                          TextStyle(fontWeight: FontWeight.bold, fontSize: 15),
                    ),
                  ),
                  const SizedBox(
                    height: 15,
                  ),
                  const Center(
                    child: Text(
                      "Kindly Attention SJC Subscriber's,This \n Scheme is only available till November \n 2022.If you are already existing in this",
                      style: TextStyle(fontSize: 12.5),
                    ),
                  ),
                  const Center(
                    child: Text(
                      "Scheme you can continue",
                      style: TextStyle(fontSize: 12.5),
                    ),
                  ),
                  const SizedBox(
                    height: 10,
                  ),
                  Row(
                    mainAxisAlignment: MainAxisAlignment.end,
                    children: [
                      Container(
                        padding: const EdgeInsets.only(right: 15),
                        child: TextButton(
                          child: const Text(
                            'Close',
                            style:
                                TextStyle(fontSize: 18, color: Colors.black87),
                          ),
                          onPressed: () {
                            Navigator.of(context).pop();
                          },
                        ),
                      ),
                      Container(
                        padding: const EdgeInsets.only(right: 15),
                        child: TextButton(
                          child: const Text(
                            'Yes',
                            style:
                                TextStyle(fontSize: 18, color: Colors.black87),
                          ),
                          onPressed: () {
                            Navigator.of(context).push(
                              MaterialPageRoute(
                                builder: (BuildContext context) {
                                  return const CardOneImage();
                                },
                              ),
                            );
                          },
                        ),
                      ),
                    ],
                  ),
                ],
              ),
            )
          ],
        );
      },
    );
  }

  Future whatsappPop() {
    return showDialog(
      context: context,
      builder: (context) {
        return const WhatsappAlertDialog();
      },
    );
  }

  Future locationPopup() {
    return showDialog(
      context: context,
      builder: (context) {
        return const LocationAlertDialog();
      },
    );
  }

  Future callPopup() {
    return showDialog(
      context: context,
      builder: (context) {
        return AlertDialog(
          actions: [
            Container(
              padding: const EdgeInsets.all(6.0),
              child: Column(
                children: [
                  const SizedBox(
                    height: 5,
                  ),
                  const Text(
                    'Contact Details',
                    style:
                        TextStyle(fontSize: 15.0, fontWeight: FontWeight.bold),
                  ),
                  const SizedBox(
                    height: 10,
                  ),
                  const Text(
                    'Press on the number to direct Call',
                    style: TextStyle(fontSize: 12.8),
                  ),
                  const SizedBox(
                    height: 10,
                  ),
                  Column(
                    children: [
                      Row(
                        mainAxisAlignment: MainAxisAlignment.spaceBetween,
                        children: [
                          const Text(
                            'Trichy',
                            style: TextStyle(
                                fontSize: 12.0, fontWeight: FontWeight.bold),
                          ),
                          Row(
                            children: [
                              TextButton(
                                onLongPress: () async {
                                  const number = '9361000950';
                                  await FlutterPhoneDirectCaller.callNumber(
                                      number);
                                },
                                onPressed: () {},
                                child: const Text(
                                  '9361000950',style: TextStyle(color: Colors.black),
                                ),
                              ),
                              const Icon(
                                Icons.vibration,
                                color: Color.fromARGB(255, 198, 45, 180),
                              ),
                            ],
                          ),
                        ],
                      ),
                      Row(
                        mainAxisAlignment: MainAxisAlignment.spaceBetween,
                        children: [
                          const Text(
                            'Karur',
                            style: TextStyle(
                                fontSize: 12.0, fontWeight: FontWeight.bold),
                          ),
                          Row(
                            children: [
                              TextButton(
                                onPressed: () {},
                                onLongPress: () async{
                                  const number = '8610115093';
                                  await FlutterPhoneDirectCaller.callNumber(
                                      number);
                                },
                                child: const Text('8610115093',style: TextStyle(color: Colors.black),),
                              ),
                              const Icon(
                                Icons.vibration,
                                color:Color.fromARGB(255, 198, 45, 180),
                              ),
                            ],
                          ),
                        ],
                      ),
                      Row(
                        mainAxisAlignment: MainAxisAlignment.spaceBetween,
                        children: [
                          const Text(
                            'Namakkal',
                            style: TextStyle(
                                fontSize: 12.0, fontWeight: FontWeight.bold),
                          ),
                          Row(
                            children: [
                              TextButton(
                                onPressed: () {},
                                onLongPress: () async{
                                  const number = '7339557145';
                                  await FlutterPhoneDirectCaller.callNumber(
                                      number);
                                },
                                child: const Text('7339557145',style: TextStyle(color: Colors.black),),
                              ),
                              const Icon(
                                Icons.vibration,
                                color:Color.fromARGB(255, 198, 45, 180),
                              ),
                            ],
                          ),
                        ],
                      ),
                      Row(
                        mainAxisAlignment: MainAxisAlignment.spaceBetween,
                        children: [
                          const Text(
                            'Madurai',
                            style: TextStyle(
                                fontSize: 12.0, fontWeight: FontWeight.bold),
                          ),
                          Row(
                            children: [
                              TextButton(
                                onPressed: () {},
                                onLongPress: () async{
                                  const number = '8838336941';
                                  await FlutterPhoneDirectCaller.callNumber(
                                      number);
                                },
                                child: const Text('8838336941',style: TextStyle(color: Colors.black),),
                              ),
                              const Icon(
                                Icons.vibration,
                                color:Color.fromARGB(255, 198, 45, 180),
                              ),
                            ],
                          ),
                        ],
                      ),
                      Row(
                        mainAxisAlignment: MainAxisAlignment.spaceBetween,
                        children: [
                          const Text(
                            'Salem',
                            style: TextStyle(
                                fontSize: 12.0, fontWeight: FontWeight.bold),
                          ),
                          Row(
                            children: [
                              TextButton(
                                onPressed: () {},
                                onLongPress: () async{
                                  const number = '9600796598';
                                  await FlutterPhoneDirectCaller.callNumber(
                                      number);
                                },
                                child: const Text('9600796598',style: TextStyle(color: Colors.black),),
                              ),
                              const Icon(
                                Icons.vibration,
                                color:Color.fromARGB(255, 198, 45, 180),
                              ),
                            ],
                          ),
                        ],
                      ),
                      Row(
                        mainAxisAlignment: MainAxisAlignment.spaceBetween,
                        children: [
                          const Text(
                            'Thanjavur',
                            style: TextStyle(
                                fontSize: 12.0, fontWeight: FontWeight.bold),
                          ),
                          Row(
                            children: [
                              TextButton(
                                onPressed: () {},
                                onLongPress: () async{
                                  const number = '9943720930';
                                  await FlutterPhoneDirectCaller.callNumber(
                                      number);
                                },
                                child: const Text('9943720930',style: TextStyle(color: Colors.black),),
                              ),
                              const Icon(
                                Icons.vibration,
                                color:Color.fromARGB(255, 198, 45, 180),
                              ),
                            ],
                          ),
                        ],
                      ),
                      const SizedBox(
                        height: 10,
                      ),
                      const Row(
                        mainAxisAlignment: MainAxisAlignment.center,
                        children: [
                          Text(
                            'Toll Free No : 1800 425 1432',
                            style: TextStyle(
                                fontSize: 14.0, fontWeight: FontWeight.bold),
                          ),
                        ],
                      ),
                    ],
                  ),
                  // PhoneNumber('+917339557145'),

                  const SizedBox(
                    height: 15,
                  ),
                  SizedBox(
                    child: Row(
                      mainAxisAlignment: MainAxisAlignment.end,
                      children: [
                        TextButton(
                            onPressed: () {
                              Navigator.of(context).pop();
                            },
                            style: TextButton.styleFrom(
                              // padding: const EdgeInsets.fromLTRB(
                              //     30, 15, 30, 15),
                              textStyle: const TextStyle(fontSize: 14.0),
                            ),
                            child: const Text('Cancel'))
                      ],
                    ),
                  ),
                ],
              ),
            ),
          ],
        );
      },
    );
  }
}

WhatsAppNumber(String s) {
  return GestureDetector(
    onLongPress: () {
      launch('whatsapp://send?phone=$s&text=hi');
    },
  );
}
