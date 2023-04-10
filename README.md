import 'package:flutter/material.dart';
void main() {
runApp(
const MaterialApp(
debugShowCheckedModeBanner: false,
home: AgeCalculator(),
),
);
}
class AgeCalculator extends StatefulWidget {
const AgeCalculator({Key? key}) : super(key: key);
@override
State<AgeCalculator> createState() => _AgeCalculatorState();
}
class _AgeCalculatorState extends State<AgeCalculator> {
DateTime date = DateTime.now();
String DD = "00";
String MM = "00";
String YY = "00";
String pDate = "00";
String pMonth = "00";
String pYear = "00";
TextEditingController dateController = TextEditingController();
TextEditingController monthController = TextEditingController();
TextEditingController yearController = TextEditingController();
TextStyle dispText = const TextStyle(
fontSize: 20,
fontWeight: FontWeight.bold,
color: Colors.white,
);
List<String> months = [
"Jan",
"Feb",
"Mar",
"Apr",
"May",
"Jun",
"Jul",
"Aug",
"Sep",
"Oct",
"Nev",
"Des",
];
@override
Widget build(BuildContext context) {
return Scaffold(
resizeToAvoidBottomInset: false,
appBar: AppBar(
title: Text(
"Age Calculator",
style: TextStyle(
fontWeight: FontWeight.bold,
fontSize: 25,
),
),
centerTitle: true,
backgroundColor: Color(0xff203A43),
),
body: Column(
children: [
Expanded(
flex: 1,
child: Container(
margin: EdgeInsets.all(10),
alignment: Alignment.centerLeft,
child: Column(
crossAxisAlignment: CrossAxisAlignment.start,
children: [
const Text(
"Today's Date",
style: TextStyle(
fontSize: 15,
fontWeight: FontWeight.bold,
),
),
const Spacer(),
Container(
padding: const EdgeInsets.only(left: 15),
height: 50,
alignment: Alignment.centerLeft,
decoration: BoxDecoration(
border: Border.all(),
borderRadius: BorderRadius.circular(10),
),
child: Text(
"${date.day} ${months[date.month - 1]}, ${date.year}",
style: const TextStyle(
color: Color(0xff1C003E),
fontSize: 20,
fontWeight: FontWeight.w600,
),
),
),
],
),
),
),
Expanded(
flex: 1,
child: Container(
child: Container(
child: Align(
alignment: Alignment.centerLeft,
child: Column(
crossAxisAlignment: CrossAxisAlignment.start,
children: [
const Text(
" Date Of Birth",
style: TextStyle(
fontSize: 15,
fontWeight: FontWeight.bold,
),
),
Row(
children: [
const Spacer(
flex: 1,
),
Expanded(
flex: 9,
child: Container(
decoration: BoxDecoration(),
child: TextField(
controller: dateController,
decoration: InputDecoration(
hintText: " DD",
border: OutlineInputBorder(
borderRadius: BorderRadius.circular(10),
),
),
onChanged: (value) {
setState(() {
DD = value;
print(DD);
});
},
),
),
),
const Spacer(
flex: 1,
),
Expanded(
flex: 9,
child: Container(
decoration: BoxDecoration(),
child: TextField(
controller: monthController,
decoration: InputDecoration(
hintText: " MM",
border: OutlineInputBorder(
borderRadius: BorderRadius.circular(10),
),
),
onChanged: (value) {
setState(() {
MM = value;
print(MM);
});
},
),
),
),
const Spacer(
flex: 1,
),
Expanded(
flex: 9,
child: Container(
decoration: BoxDecoration(),
child: TextField(
controller: yearController,
decoration: InputDecoration(
hintText: " YYYY",
border: OutlineInputBorder(
borderRadius: BorderRadius.circular(10),
),
),
onChanged: (value) {
setState(() {
YY = value;
print(YY);
});
},
),
),
),
const Spacer(
flex: 1,
),
],
)
],
),
),
),
),
),
Expanded(
flex: 1,
child: Container(
padding: EdgeInsetsDirectional.all(10),
child: Row(
children: [
Expanded(
child: InkWell(
onTap: () {
setState(() {
dateController.clear();
monthController.clear();
yearController.clear();
DD = "00";
MM = "00";
YY = "00";
});
},
child: Container(
height: 60,
width: 100,
decoration: BoxDecoration(
border: Border.all(
color: Color(0xff13547A),
),
borderRadius: BorderRadius.circular(15),
),
alignment: Alignment.center,
child: const Text(
"Clear",
style: TextStyle(
fontSize: 25,
fontWeight: FontWeight.bold,
),
),
),
),
),
const SizedBox(
width: 8,
),
Expanded(
child: InkWell(
onTap: () {
setState(() {
pYear = (date.year - int.parse(YY)).toString();
pMonth = (date.month >= int.parse(MM))
? (date.month - int.parse(MM)).toString()
: (int.parse(MM) - date.month - 1).toString();
pDate = (date.day >= int.parse(DD))
? (date.day - int.parse(DD)).toString()
: (int.parse(DD) - date.day - 1).toString();
});
pMonth = (date.month >= int.parse(MM))
? (date.month - int.parse(MM)).toString()
: (int.parse(MM) - date.month ).toString();
pDate = (date.day >= int.parse(DD))
? (date.day - int.parse(DD)).toString()
: (int.parse(DD) - date.day).toString();
},
child: Container(
height: 60,
decoration: BoxDecoration(
color: Color(0xff13547A),
border: Border.all(),
borderRadius: BorderRadius.circular(15),
),
alignment: Alignment.center,
child: const Text(
"Calculate",
style: TextStyle(
fontSize: 25,
color: Colors.white,
fontWeight: FontWeight.bold,
),
),
),
),
),
],
),
),
),
Expanded(
flex: 2,
child: Container(
margin: EdgeInsetsDirectional.all(10),
child: Column(
crossAxisAlignment: CrossAxisAlignment.start,
children: [
const Text(
"Present Age",
style: TextStyle(
fontSize: 15,
fontWeight: FontWeight.bold,
),
),
Container(
height: 140,
decoration: BoxDecoration(
gradient: const LinearGradient(
colors: [
Color(0xff13547A),
Color(0xff203A43),
],
),
borderRadius: BorderRadius.circular(10),
),
child: Row(
mainAxisAlignment: MainAxisAlignment.spaceEvenly,
children: [
Column(
mainAxisAlignment: MainAxisAlignment.center,
children: [
Text(
" $pYear",
style: dispText,
),
Text(
"Year",
style: dispText,
),
],
),
Column(
mainAxisAlignment: MainAxisAlignment.center,
children: [
Text(
"$pMonth",
style: dispText,
),
Text(
"MM",
style: dispText,
),
],
),
Column(
mainAxisAlignment: MainAxisAlignment.center,
children: [
Text(
"$pDate",
style: dispText,
),
Text(
"DD",
style: dispText,
),
],
),
],
),
),
],
),
),
),
Expanded(
flex: 2,
child: Container(
margin: EdgeInsetsDirectional.all(10),
child: Column(
crossAxisAlignment: CrossAxisAlignment.start,
children: [
const Text(
"Next Birthday",
style: TextStyle(
fontSize: 15,
fontWeight: FontWeight.bold,
),
),
Container(
height: 140,
decoration: BoxDecoration(
gradient: const LinearGradient(
colors: [
Color(0xff6BBED9),
Color(0xff006ACB),
],
),
borderRadius: BorderRadius.circular(10),
),
child: Row(
mainAxisAlignment: MainAxisAlignment.spaceEvenly,
children: [
Column(
mainAxisAlignment: MainAxisAlignment.center,
children: [
Text(
"$pMonth",
style: dispText,
),
Text(
"MM",
style: dispText,
),
],
),
Column(
mainAxisAlignment: MainAxisAlignment.center,
children: [
Text(
"$pDate",
style: dispText,
),
Text(
"DD",
style: dispText,
),
],
),
],
),
),
],
),
),
),
],
),
);
}
}