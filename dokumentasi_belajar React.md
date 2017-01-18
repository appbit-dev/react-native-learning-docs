#Dokumentasi Belajar React Native
#### 18 Desember 2016 #####
### Aji Pratama ###

#


## **Konfigurasi & Persiapan Project **
###Install npm
Sebelum memulai belajar React Native mari persiapkan dulu Projectnya, kita install  dulu Javascript environment diantaranta npm, nodejs, dan homebrow  ketikan perintah dibawah pada terminal :

	$sudo apt-get install npm
	$sudo apt-get install node
	$sudo apt-get install homebrew


###Install npm env brew
Kemudian instal package npm watchman dan flow :

	$brew install watchman
	$brew install flow

###Install React Command Line
Install react-cli  untuk memudahkan kita membuat project react-native baru nantinya, jadi kita tinggal ketikan perintah beserta nama projectnya apabila sudah diinstall :

	$npm install -g react-native-cli

###Install androidSDK****
Kalau yang ini butuh kuota data yang lumayan banyak, untuk lebih jelasnya teman-teman bisa cari tutorialnya di dokumentasi android development, saya hanya memberikan list-list apa saja yang di perlukan :

	- $export ANDROID_HOME=/usr/local/opt/android-sdk #Setting Path
	- Android SDK Build-tools version 23.0.1
	- Android 6.0 (API 23)
	- Android Support	
	- Intel	x86 Atom System	Image (for Android 5.1.1–API 22)
	- Intel	x86 Emulator Accelerator (HAXM installer)

###Menginisialisasikan/membuat Project React
Kemudian yang membuat project baru react-native, karena tadi kita sudah install react-native-cli teman-teman bisa langsung panggil perintahnya :

	$react-native init <nama-project> 

###Running Untuk Operasional Development (Suistanable)
Yang ini akan terus kita gunakan apabila kita memulai development project, 
#### untuk memulai emulator androidnya

	$android avd
	
####untuk memulai project react-native
	
	$react-native run-android (Running aplikasi android di React)

####yang ini untuk menyalakan server javascriptnya

	$npm start (menyalakan server npm)

###Membuat program "Hello Coeg":
Sebelum membuat aplikasi beneran mari kita buat program "Hello Coeg" pada file index.android.js:

###index.andoid.js :

~~~~
import React, { Component } from 'react';
import { AppRegistry, Text } from 'react-native';

class hellocoeg extends Component {
	 render() {
    		return (
      			<Text>Hello Coeg</Text>
		)
	}
}
AppRegistry.registerComponent('hellocoeg', () => hellocoeg);
~~~~

Setelah di buat simpan file nya dan arahkan kursor pada emulator lalu tekan R (dua kali).
#

##**React Basic**

Setelah selesai konfigurasi project, selanjutnya kita akan memahami basic-basic pada react native.

### **1. Props & State**
**Props : ** adalah properti atau variabel yang berasal dari luar class atau class parent. 


~~~~
import React, { Component } from 'react';
import { AppRegistry, Image, Text, View } from 'react-native';

//Class ini mendefinisikan props, dann di panggil ke klass utama HelloCoeg
class PropCoba extends Component {
  render() {
    return (
      <Text>Hello {this.props.name}!</Text> 
    );
  }
}

class relearn extends Component {
  render() {
    let pic = {
      uri: 'https://avatar-cdn.atlassian.com/31b95d6225e05ebea729d0ff5ac0e6cf?s=256&ts=1482230425'
    };
    return (
      <View style={{alignItems: 'center'}}>
        <Image source ={ pic } style = {{ width: 150, height: 200 }} /> 
        <PropCoba name='Aji' />     
        <PropCoba name='Pratama' />
        <PropCoba name='Haha' />
      </View>
    );
  }
}

AppRegistry.registerComponent('relearn', ()=> relearn)

~~~~

Dari penggalan code di atas dapat kita lihat kurang lebih yang ada di dalam Class PropCoba merupakan props, yang kemudian dipanggil oleh Class utama, yang kemudian nama Class PropCoba menjadi sebuah Komponen yang bisa dipanggil dengan tag ala-ala ML (markup language ada gininya <>).

#

###**State : ** adalah sebuah properti atau variabel yang didefinisikan di dalam sebuah class.

~~~~
import React, { Component } from 'react';
import { AppRegistry, Text, View } from 'react-native';

class RelearnFunc extends Component {
  constructor(props){
    super(props);
    this.state = {showText: true};
    //Menyembunyikan state ini setiap sekian detik
    setInterval(() => {
      this.setState({ showText: !this.state.showText });
    }, 1000);
  }

  render() {
    let display = this.state.showText ? this.props.text : ' ';
    return (
      <Text>{ display }</Text>
    );
  }
}

class relearn extends Component {
  render() {
    return (
      <View>
        <RelearnFunc text='Aji' />
        <RelearnFunc text='Pratama' />
        <RelearnFunc text='Adalah programmer males paling ganteng'/>
        <RelearnFunc text='di Galaxy BimaSakti' />
      </View>
    );
  }
}

AppRegistry.registerComponent('relearn', ()=> relearn)

~~~~

Kita telah membuat Class yang diberi nama RelearnFunc yang kemudian dipanggil sebagai komponen dengan nama <RelearnFunc> dari sini bisa kita lihat bagaimana di dalam class RelearnFunc terdapat operasi fungsi yang memungkinkan Text yang ada di dalam class utama beroperasi nge-Blink (kedap kedip).

~~~~
** Nama Class yang di jadikan komponen harus di awali huruf kapital
~~~~

###**2. Styling **
Styling pada react-native kurang lebih hampir mirip dengan styling pada css hanya perbedaan cara penulisan, misalkan pada css "*font-color*" nhah di react-native itu "*fontColor*" jadi pemisiahan kata cuma di ganti dari dash(-) menjadi camelcase. Berikut contoh codenya :
~~~~
import React, { Component } from 'react';
import { AppRegistry, StyleSheet, Text, View } from 'react-native';

class relearn extends Component {
  render() {
    return (
      <View>
        <Text style={setail.merah}>Merah Ajah</Text>
        <Text style={setail.ijogede}>Ijogede Ajah</Text>
        <Text style={[setail.ijogede, setail.merah]}>Ijogede duluan, merah belakangan</Text>
        <Text style={[setail.merah, setail.ijogede]}>Merah duluan, ijoGede belakangan</Text>
    </View>
    );
  }
}

const setail = StyleSheet.create({
  ijogede: {
    color: '#219922',
    fontWeight: 'bold',
    fontSize: 30,
    textAlign: 'center',
  },

  merah : {
    color: 'rgb(200, 50, 50)',
    textAlign: 'left',
  }
});

AppRegistry.registerComponent('relearn', ()=> relearn)

~~~~
Code di atas menjelaskan kalau kita memiliki sebuah style diberi nama *setail*, nhah di dalam *setail* terdapat 2 style yang di beri nama *ijogede* dan *merah* lalu style tersebut bisa di panggil dengan cara "*style={setail.merah}*".
Yang perlu di perhatikan adalah jangan lupan import "*StyleSheet*" pada header code. mudah kan? Cuma sedikit ganti penulisan apabila kawan-kawan sudah minimal tahu css.

Kali ini Height dan Weight:
 
 
~~~~ 
import React, { Component } from 'react';
import { AppRegistry, StyleSheet, Text, View } from 'react-native';

class relearn extends Component {
  render() {
    return (
      <View style={{flex: 1}}>
          <View style={{flex: 1, backgroundColor: 'skyblue'}}></View>
          <View style={{flex: 2, backgroundColor: 'powderblue'}}></View>
          <View style={{flex: 3, backgroundColor: 'steelblue' }}></View>
    </View>
      // <View>
      //       <View style={{width: 50, height:50, backgroundColor: 'skyblue'}} ></View>
      //       <View style={{width: 100, height:100, backgroundColor: 'powderblue'}}></View>
      //       <View style={{width: 150, height:150, backgroundColor: 'steelblue'}}></View>
      // </View>
    );
  }
}


AppRegistry.registerComponent('relearn', ()=> relearn)
~~~~


Nhah selanjutnya adalah Layout dengan flexbox:
kita bisa gunakan 
- flexDirection : row (kesamping), dan column (vertical kebawah),
- justifyContent : center,
- alignItems: center.

~~~~
import React, { Component } from 'react';
import { AppRegistry, StyleSheet, Text, View } from 'react-native';

class relearn extends Component {
  render() {
    return (
      <View style={{
          flex: 1,
          flexDirection: 'column',
          justifyContent: 'center',
          alignItems: 'center',
      }}>
        <View style={{width: 50, height: 50, backgroundColor: 'steelblue'}}></View>
        <View style={{width: 50, height: 50, backgroundColor: 'skyblue'}}></View>
        <View style={{width: 50, height: 50, backgroundColor: 'powderblue'}}></View>
    </View>
    );
  }
}


AppRegistry.registerComponent('relearn', ()=> relearn)

~~~~

