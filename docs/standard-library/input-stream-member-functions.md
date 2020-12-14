---
description: En savoir plus sur les fonctions membres de flux d’entrée
title: Fonctions membres de flux d'entrée
ms.date: 07/19/2019
helpviewer_keywords:
- input stream objects
- input streams, member functions
ms.assetid: b4b9465d-0da9-4ccf-859d-72a68418982e
ms.openlocfilehash: 8b75470d39e5c376da497f721c725eaad8424b3d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231600"
---
# <a name="input-stream-member-functions"></a>Fonctions membres de flux d'entrée

Les fonctions membres de flux d’entrée sont utilisées pour l’entrée de disque.

## <a name="open"></a><a name="vclrftheopenfunctionforinputstreamsanchor11"></a> afficher

Si vous utilisez un flux de fichier d’entrée ( `ifstream` ), vous devez associer ce flux à un fichier disque spécifique. Vous pouvez le faire dans le constructeur, ou vous pouvez utiliser la `open` fonction. Dans les deux cas, les arguments sont les mêmes.

Vous spécifiez généralement un indicateur [ios_base :: OpenMode](../standard-library/ios-base-class.md#openmode) lorsque vous ouvrez le fichier associé à un flux d’entrée (le mode par défaut est `ios::in` ). Pour obtenir la liste des `openmode` indicateurs, consultez [ios_base :: OpenMode](../standard-library/ios-base-class.md#openmode). Les indicateurs peuvent être combinés avec l’opérateur de bits OR ( &#124; ).

Pour lire un fichier, utilisez d’abord la `fail` fonction membre pour déterminer s’il existe :

```cpp
istream ifile("FILENAME");

if (ifile.fail())
// The file does not exist ...
```

## <a name="get"></a><a name="vclrfthegetfunctionanchor12"></a> Télécharger

La fonction membre non mise en forme `get` fonctionne comme l' `>>` opérateur avec deux exceptions. Tout d’abord, la `get` fonction inclut des espaces blancs, tandis que l’extracteur exclut les espaces blancs lorsque l' `skipws` indicateur est défini (valeur par défaut). Deuxièmement, la `get` fonction est moins susceptible de provoquer le vidage d’un flux de sortie lié ( `cout` , par exemple).

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

### <a name="sample-output"></a>Exemple de sortie

```Output
1234
```

## <a name="getline"></a><a name="vclrfthegetlinefunctionanchor13"></a> getline

La `getline` fonction membre est semblable à la `get` fonction. Toutes deux autorisent un troisième argument qui spécifie le caractère de fin pour l’entrée. La valeur par défaut est le caractère de saut de ligne. Ces deux fonctions réservent un caractère pour le caractère de fin obligatoire. Toutefois, `get` conserve le caractère de fin dans le flux et `getline` supprime le caractère de fin.

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

## <a name="read"></a><a name="vclrfthereadfunctionanchor14"></a> en lecture

La `read` fonction membre lit les octets d’un fichier dans une zone de mémoire spécifiée. L’argument de longueur détermine le nombre d’octets lus. Si vous n’incluez pas cet argument, la lecture s’arrête quand la fin du fichier physique est atteinte ou, dans le cas d’un fichier en mode texte, quand un caractère `EOF` incorporé est lu.

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

Le programme suppose que les enregistrements de données sont mis en forme exactement comme spécifié par la structure sans retour chariot ou caractère de saut de ligne de fin.

## <a name="seekg-and-tellg"></a><a name="vclrftheseekgandtellgfunctionsanchor7"></a> seekg et tellg

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

Pour utiliser `seekg` pour implémenter des systèmes de gestion de données orientés enregistrement, multipliez la taille d’enregistrement de longueur fixe par le numéro d’enregistrement pour obtenir la position d’octet par rapport à la fin du fichier, puis utilisez l' `get` objet pour lire l’enregistrement.

La fonction membre `tellg` retourne la position actuelle du fichier pour la lecture. Cette valeur est de type `streampos` , un **`typedef`** défini dans \<iostream> . L’exemple suivant lit un fichier et affiche des messages indiquant la position des espaces.

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

## <a name="close"></a><a name="vclrftheclosefunctionforinputstreamsanchor15"></a> plus

La `close` fonction membre ferme le fichier de disque associé à un flux de fichier d’entrée et libère le handle de fichier du système d’exploitation. Le [`ifstream`](../standard-library/basic-ifstream-class.md) destructeur ferme le fichier pour vous, mais vous pouvez utiliser la `close` fonction si vous devez ouvrir un autre fichier pour le même objet de flux.

## <a name="see-also"></a>Voir aussi

[Flux d’entrée](../standard-library/input-streams.md)
