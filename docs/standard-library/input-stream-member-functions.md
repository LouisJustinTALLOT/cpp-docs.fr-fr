---
title: Fonctions membres de flux d’entrée | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- input stream objects
- input streams, member functions
ms.assetid: b4b9465d-0da9-4ccf-859d-72a68418982e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 57288e7eb85e3d23fe8790ac3097cab82acdcf8b
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954667"
---
# <a name="input-stream-member-functions"></a>Fonctions membres de flux d'entrée

Les fonctions membres de flux d’entrée sont utilisées pour l’entrée de disque. Il s’agit des fonctions membres suivantes :

- [Fonction open pour les flux d’entrée](#vclrftheopenfunctionforinputstreamsanchor11)

- [La fonction modèle get](#vclrfthegetfunctionanchor12)

- [Getline](#vclrfthegetlinefunctionanchor13)

- [La lecture](#vclrfthereadfunctionanchor14)

- [Fonctions seekg et tellg](#vclrftheseekgandtellgfunctionsanchor7)

- [Fonction close pour les flux d’entrée](#vclrftheclosefunctionforinputstreamsanchor15)

## <a name="vclrftheopenfunctionforinputstreamsanchor11"></a> Fonction open pour les flux d’entrée

Si vous utilisez un flux d’entrée (ifstream), vous devez associer ce flux à un fichier de disque spécifique. Vous pouvez le faire dans le constructeur, ou vous pouvez utiliser le `open` (fonction). Dans les deux cas, les arguments sont les mêmes.

Vous spécifiez généralement un [ios_base::openmode](../standard-library/ios-base-class.md#openmode) indicateur lorsque vous ouvrez le fichier associé à un flux d’entrée (le mode par défaut est `ios::in`). Pour obtenir la liste de la `open_mode` indicateurs, consultez [l’ouvrir](#vclrftheopenfunctionforinputstreamsanchor11). Les indicateurs peuvent être combinés avec l’opérateur de bits OR ( &#124; ).

Pour lire un fichier, utilisez d’abord la `fail` fonction membre pour déterminer si elle existe :

```cpp
istream ifile("FILENAME");

if (ifile.fail())
// The file does not exist ...
```

## <a name="vclrfthegetfunctionanchor12"></a> La fonction modèle get

La non mise en forme `get` fonction membre fonctionne comme le `>>` opérateur à deux exceptions près. Tout d’abord, le `get` fonction comprend des espaces blancs, alors que l’extracteur exclut les espaces blancs lors de la `skipws` indicateur est défini (la valeur par défaut). Ensuite, le `get` fonction est moins susceptible de causer un flux de sortie lié (`cout`, par exemple) d’être vidées.

Une variante de la `get` fonction spécifie une adresse de mémoire tampon et le nombre maximal de caractères à lire. Ceci est utile pour limiter le nombre de caractères envoyés à une variable spécifique, comme le montre cet exemple :

```cpp
// ioo_get_function.cpp
// compile with: /EHsc
// Type up to 24 characters and a terminating character.
// Any remaining characters can be extracted later.
#include <iostream>
using namespace std;

int main()
{
   char line[25];
   cout << " Type a line terminated by carriage return\n>";
   cin.get( line, 25 );
   cout << line << endl;
}
```

### <a name="input"></a>Entrée

```Input
1234
```

### <a name="sample-output"></a>Résultat de l'exemple

```Output
1234
```

## <a name="vclrfthegetlinefunctionanchor13"></a> Getline

Le `getline` fonction membre est similaire à la `get` (fonction). Toutes deux autorisent un troisième argument qui spécifie le caractère de fin pour l’entrée. La valeur par défaut est le caractère de saut de ligne. Ces deux fonctions réservent un caractère pour le caractère de fin obligatoire. Toutefois, `get` laisse le caractère de fin dans le flux et `getline` supprime le caractère de fin.

L’exemple suivant spécifie un caractère de fin pour le flux d’entrée :

```cpp
// getline_func.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char line[100];
   cout << " Type a line terminated by 't'" << endl;
   cin.getline( line, 100, 't' );
   cout << line;
}
```

### <a name="input"></a>Entrée

```Input
test
```

## <a name="vclrfthereadfunctionanchor14"></a> La lecture

Le `read` fonction membre lit les octets à partir d’un fichier à la zone de mémoire spécifiée. L’argument de longueur détermine le nombre d’octets lus. Si vous n’incluez pas cet argument, la lecture s’arrête quand la fin du fichier physique est atteinte ou, dans le cas d’un fichier en mode texte, quand un caractère `EOF` incorporé est lu.

Cet exemple lit un enregistrement binaire à partir d’un fichier de paie dans une structure :

```cpp
#include <fstream>
#include <iostream>
using namespace std;

int main()
{
   struct
   {
      double salary;
      char name[23];
   } employee;

   ifstream is( "payroll" );
   if( is ) {  // ios::operator void*()
      is.read( (char *) &employee, sizeof( employee ) );
      cout << employee.name << ' ' << employee.salary << endl;
   }
   else {
      cout << "ERROR: Cannot open file 'payroll'." << endl;
   }
}
```

Le programme part du principe que les enregistrements de données sont mis en forme exactement comme spécifié par la structure, sans caractère de retour chariot ou de saut de ligne de fin.

## <a name="vclrftheseekgandtellgfunctionsanchor7"></a> Fonctions seekg et tellg

Les flux de fichiers d’entrée conservent un pointeur interne vers la position suivante dans le fichier où les données doivent être lues. Vous définissez ce pointeur avec la fonction `seekg`, comme indiqué ici :

```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main( )
{
   char ch;

   ifstream tfile( "payroll" );
   if( tfile ) {
      tfile.seekg( 8 );        // Seek 8 bytes in (past salary)
      while ( tfile.good() ) { // EOF or failure stops the reading
         tfile.get( ch );
         if( !ch ) break;      // quit on null
         cout << ch;
      }
   }
   else {
      cout << "ERROR: Cannot open file 'payroll'." << endl;
   }
}
```

Pour utiliser `seekg` pour implémenter des systèmes de gestion de données orientés enregistrements, multipliez la taille d’enregistrement de longueur fixe par le numéro d’enregistrement pour obtenir la position d’octet par rapport à la fin du fichier, puis utiliser le `get` objet à lire l’enregistrement.

La fonction membre `tellg` retourne la position actuelle du fichier pour la lecture. Cette valeur est de type `streampos`, un `typedef` défini dans \<iostream>. L’exemple suivant lit un fichier et affiche des messages indiquant la position des espaces.

```cpp
#include <fstream>
#include <iostream>
using namespace std;

int main( )
{
   char ch;
   ifstream tfile( "payroll" );
   if( tfile ) {
       while ( tfile.good( ) ) {
          streampos here = tfile.tellg();
          tfile.get( ch );
          if ( ch == ' ' )
             cout << "\nPosition " << here << " is a space";
       }
   }
   else {
      cout << "ERROR: Cannot open file 'payroll'." << endl;
   }
}
```

## <a name="vclrftheclosefunctionforinputstreamsanchor15"></a> Fonction close pour les flux d’entrée

Le `close` fonction membre ferme le fichier de disque associé à un flux de fichier d’entrée et libère le handle de fichier du système d’exploitation. Le [ifstream](../standard-library/basic-ifstream-class.md) destructeur ferme le fichier pour vous, mais vous pouvez utiliser le `close` fonctionner si vous devez ouvrir un autre fichier pour le même objet de flux de données.

## <a name="see-also"></a>Voir aussi

[Flux d’entrée](../standard-library/input-streams.md)<br/>
