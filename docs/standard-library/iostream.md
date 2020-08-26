---
title: '&lt;iostream&gt;'
ms.date: 09/20/2017
f1_keywords:
- <iostream>
- iostream/std::cerr
- iostream/std::cin
- iostream/std::clog
- iostream/std::cout
- iostream/std::wcerr
- iostream/std::wcin
- iostream/std::wclog
- iostream/std::wcout
helpviewer_keywords:
- iostream header
ms.assetid: de5d39e1-7e77-4b55-bcd1-7c77b41515c8
ms.openlocfilehash: 5805d441b4fc2fc2927b57f4d94ba8b8ccecb22a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845469"
---
# <a name="ltiostreamgt"></a>&lt;iostream&gt;

Déclare des objets qui contrôlent la lecture et l'écriture des flux standard. Il s’agit souvent du seul en-tête dont vous avez besoin pour effectuer une entrée et une sortie à partir d’un programme C++.

## <a name="syntax"></a>Syntaxe

```cpp
#include <iostream>
```

> [!NOTE]
> La \<iostream> bibliothèque utilise les `#include <ios>` instructions,, `#include <streambuf>` `#include <istream>` et `#include <ostream>` .

## <a name="remarks"></a>Notes

Les objets se répartissent en deux groupes :

- [CIN](#cin), [cout](#cout), [CERR](#cerr)et [obstruent](#clog) des octets orientés octet, en procédant à des transferts conventionnels de type « octet à un moment ».

- [wcin](#wcin), [wcout](#wcout), [wcerr](#wcerr) et [wclog](#wclog) sont orientés largeur et traduisent vers et à partir des caractères larges que le programme manipule en interne.

Une fois que vous effectuez certaines opérations sur un flux, telles que l’entrée standard, vous ne pouvez pas effectuer d’opérations d’une orientation différente sur le même flux. Par exemple, un programme ne peut pas fonctionner de façon interchangeable à la fois sur [CIN](#cin) et [wcin](#wcin).

Tous les objets déclarés dans cet en-tête partagent une propriété particulière : vous pouvez supposer qu’ils sont construits avant les objets statiques que vous définissez, dans une unité de traduction qui comprend \<iostream> . De même, vous pouvez supposer que ces objets ne sont pas détruits avant les destructeurs pour les objets statiques que vous définissez. (Toutefois, les flux de sortie sont vidés durant l’arrêt du programme.) Par conséquent, vous pouvez en toute sécurité lire ou écrire dans les flux standard avant le démarrage du programme et après l’arrêt du programme.

Toutefois, cette garantie n’est pas universelle. Un constructeur statique peut appeler une fonction dans une autre unité de traduction. La fonction appelée ne peut pas supposer que les objets déclarés dans cet en-tête ont été construits, étant donné l’ordre incertain dans lequel les unités de traduction participent à la construction statique. Pour utiliser ces objets dans ce contexte, vous devez d’abord construire un objet de classe [ios_base::Init](../standard-library/ios-base-class.md#init).

### <a name="global-stream-objects"></a>Objets de flux global

|Nom|Description|
|-|-|
|[cerr](#cerr)|Spécifie le flux global `cerr`.|
|[CIN](#cin)|Spécifie le flux global `cin`.|
|[Clog](#clog)|Spécifie le flux global `clog`.|
|[cout](#cout)|Spécifie le flux global `cout`.|
|[wcerr](#wcerr)|Spécifie le flux global `wcerr`.|
|[wcin](#wcin)|Spécifie le flux global `wcin`.|
|[wclog](#wclog)|Spécifie le flux global `wclog`.|
|[wcout](#wcout)|Spécifie le flux global `wcout`.|

### <a name="cerr"></a><a name="cerr"></a> CERR

L’objet `cerr` contrôle la sortie dans une mémoire tampon de flux associée à l’objet `stderr` , déclarée dans \<cstdio> .

```cpp
extern ostream cerr;
```

#### <a name="return-value"></a>Valeur renvoyée

Objet [ostream](../standard-library/ostream-typedefs.md#ostream).

#### <a name="remarks"></a>Notes

L’objet contrôle les insertions non mises en mémoire tampon dans la sortie d’erreur standard sous forme de flux d’octets. Une fois l’objet construit, l’expression `cerr.`[flags](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) est différente de zéro, et `cerr.tie() == &cout`.

#### <a name="example"></a>Exemple

```cpp
// iostream_cerr.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

void TestWide( )
{
   int i = 0;
   wcout << L"Enter a number: ";
   wcin >> i;
   wcerr << L"test for wcerr" << endl;
   wclog << L"test for wclog" << endl;
}

int main( )
{
   int i = 0;
   cout << "Enter a number: ";
   cin >> i;
   cerr << "test for cerr" << endl;
   clog << "test for clog" << endl;
   TestWide( );
}
```

### <a name="cin"></a><a name="cin"></a> CIN

Spécifie le flux global `cin`.

```cpp
extern istream cin;
```

#### <a name="return-value"></a>Valeur renvoyée

Objet [istream](../standard-library/istream-typedefs.md#istream).

#### <a name="remarks"></a>Notes

L’objet contrôle les extractions à partir de l’entrée standard en tant que flux d’octets. Une fois l’objet construit, l’appel `cin.`[tie](../standard-library/basic-ios-class.md#tie) retourne `&`[cout](#cout).

#### <a name="example"></a>Exemple

Dans cet exemple, `cin` définit le bit d’échec sur le flux lorsqu’il se trouve sur des caractères non numériques. Le programme efface le bit d’échec et supprime le caractère non valide du flux pour continuer.

```cpp
// iostream_cin.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main()
{
   int x;
   cout << "enter choice:";
   cin >> x;
   while (x < 1 || x > 4)
   {
      cout << "Invalid choice, try again:";
      cin >> x;
      // not a numeric character, probably
      // clear the failure and pull off the non-numeric character
      if (cin.fail())
      {
         cin.clear();
         char c;
         cin >> c;
      }
   }
}
```

```Output
2
```

### <a name="clog"></a><a name="clog"></a> Clog

Spécifie le flux global `clog`.

```cpp
extern ostream clog;
```

#### <a name="return-value"></a>Valeur renvoyée

Objet [ostream](../standard-library/ostream-typedefs.md#ostream).

#### <a name="remarks"></a>Notes

L’objet contrôle les insertions mises en mémoire tampon dans la sortie d’erreur standard sous forme de flux d’octets.

#### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `clog`, consultez [cerr](#cerr).

### <a name="cout"></a><a name="cout"></a> cout

Spécifie le flux global `cout`.

```cpp
extern ostream cout;
```

#### <a name="return-value"></a>Valeur renvoyée

Objet [ostream](../standard-library/ostream-typedefs.md#ostream).

#### <a name="remarks"></a>Notes

L’objet contrôle les insertions dans la sortie standard sous forme de flux d’octets.

#### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `cout`, consultez [cerr](#cerr).

### <a name="wcerr"></a><a name="wcerr"></a> wcerr

Spécifie le flux global `wcerr`.

```cpp
extern wostream wcerr;
```

#### <a name="return-value"></a>Valeur renvoyée

Objet [wostream](../standard-library/ostream-typedefs.md#wostream).

#### <a name="remarks"></a>Notes

L’objet contrôle les insertions non mises en mémoire tampon dans la sortie d’erreur standard sous forme de flux large. Une fois l’objet construit, l’expression `wcerr.`[flags](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) est différente de zéro.

#### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `wcerr`, consultez [cerr](#cerr).

### <a name="wcin"></a><a name="wcin"></a> wcin

Spécifie le flux global `wcin`.

```cpp
extern wistream wcin;
```

#### <a name="return-value"></a>Valeur renvoyée

Objet [wistream](../standard-library/istream-typedefs.md#wistream).

#### <a name="remarks"></a>Notes

L’objet contrôle les extractions à partir de l’entrée standard en tant que flux large. Une fois l’objet construit, l’appel `wcin.`[tie](../standard-library/basic-ios-class.md#tie) retourne `&`[wcout](#wcout).

#### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `wcin`, consultez [cerr](#cerr).

### <a name="wclog"></a><a name="wclog"></a> wclog

Spécifie le flux global `wclog`.

```cpp
extern wostream wclog;
```

#### <a name="return-value"></a>Valeur renvoyée

Objet [wostream](../standard-library/ostream-typedefs.md#wostream).

#### <a name="remarks"></a>Notes

L’objet contrôle les insertions mises en mémoire tampon dans la sortie d’erreur standard sous forme de flux large.

#### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `wclog`, consultez [cerr](#cerr).

### <a name="wcout"></a><a name="wcout"></a> wcout

Spécifie le flux global `wcout`.

```cpp
extern wostream wcout;
```

#### <a name="return-value"></a>Valeur renvoyée

Objet [wostream](../standard-library/ostream-typedefs.md#wostream).

#### <a name="remarks"></a>Notes

L'objet contrôle les insertions dans la sortie standard sous forme de flux large.

#### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `wcout`, consultez [cerr](#cerr).

Les instances de `CString` dans une instruction `wcout` doivent être converties en `const wchar_t*`, comme illustré dans l'exemple suivant.

```cpp
CString cs("meow");

wcout <<(const wchar_t*) cs <<endl;
```

Pour plus d’informations, consultez [Opérations CString de base](../atl-mfc-shared/basic-cstring-operations.md).

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[Conventions iostreams](../standard-library/iostreams-conventions.md)
