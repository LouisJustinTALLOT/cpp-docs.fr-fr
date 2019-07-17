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
ms.openlocfilehash: fa90a861194275d8c82a407e2ca8db6e757aab35
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245227"
---
# <a name="ltiostreamgt"></a>&lt;iostream&gt;

Déclare des objets qui contrôlent la lecture et l'écriture des flux standard. Cette include est souvent du seul en-tête que vous devez d’entrée et sortie à partir d’un C++ programme.

## <a name="syntax"></a>Syntaxe

```cpp
#include <iostream>
```

> [!NOTE]
> Le \<iostream > bibliothèque utilise la `#include <ios>`, `#include <streambuf>`, `#include <istream>`, et `#include <ostream>` instructions.

## <a name="remarks"></a>Notes

Les objets se répartissent en deux groupes :

- [CIN](#cin), [cout](#cout), [cerr](#cerr), et [clog](#clog) sont orientés octets transferts conventionnels d’octets au moment.

- [wcin](#wcin), [wcout](#wcout), [wcerr](#wcerr) et [wclog](#wclog) sont orientés largeur et traduisent vers et à partir des caractères larges que le programme manipule en interne.

Une fois que vous effectuez certaines opérations sur un flux, telles que l’entrée standard, vous ne pouvez pas effectuer des opérations d’une orientation différente sur le même flux. Par conséquent, un programme ne peut pas opérer indifféremment à la fois sur [cin](#cin) et [wcin](#wcin), par exemple.

Tous les objets déclarés dans cet en-tête partagent une propriété particulière, vous pouvez supposer qu’ils sont construits avant tout objet statique que vous définissez, dans une unité de traduction qui inclut \<iostream >. De même, vous pouvez supposer que ces objets ne sont pas détruits avant les destructeurs pour vous définir certains de ses objets statiques. (Les flux de sortie, cependant, sont vidés durant l'arrêt du programme.) Par conséquent, vous pouvez sans risque lire ou écrire dans les flux standard avant le démarrage et après l'arrêt du programme.

Cette garantie n’est pas universelle, toutefois. Un constructeur statique peut appeler une fonction dans une autre unité de traduction. La fonction appelée ne peut pas supposer que les objets déclarés dans cet en-tête ont été construits, étant donné l’ordre incertain dans traduction unités participent à la construction statique. Pour utiliser ces objets dans ce contexte, vous devez d’abord construire un objet de classe [ios_base::Init](../standard-library/ios-base-class.md#init).

### <a name="global-stream-objects"></a>Objets de flux global

|||
|-|-|
|[cerr](#cerr)|Spécifie le flux global `cerr`.|
|[cin](#cin)|Spécifie le flux global `cin`.|
|[clog](#clog)|Spécifie le flux global `clog`.|
|[cout](#cout)|Spécifie le flux global `cout`.|
|[wcerr](#wcerr)|Spécifie le flux global `wcerr`.|
|[wcin](#wcin)|Spécifie le flux global `wcin`.|
|[wclog](#wclog)|Spécifie le flux global `wclog`.|
|[wcout](#wcout)|Spécifie le flux global `wcout`.|

###  <a name="cerr"></a> cerr

L’objet `cerr` contrôle la sortie vers une mémoire tampon de flux associée à l’objet `stderr`, déclaré dans \<cstdio>.

```cpp
extern ostream cerr;
```

#### <a name="return-value"></a>Valeur de retour

Objet [ostream](../standard-library/ostream-typedefs.md#ostream).

#### <a name="remarks"></a>Notes

L’objet contrôle les insertions non mises en mémoire tampon dans la sortie d’erreur standard sous forme de flux d’octets. Une fois l’objet construit, l’expression `cerr.`[flags](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) est différente de zéro, et `cerr.tie() == &cout`.

#### <a name="example"></a>Exemples

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

###  <a name="cin"></a> CIN

Spécifie le flux global `cin`.

```cpp
extern istream cin;
```

#### <a name="return-value"></a>Valeur de retour

Objet [istream](../standard-library/istream-typedefs.md#istream).

#### <a name="remarks"></a>Notes

L’objet contrôle les extractions à partir de l’entrée standard en tant que flux d’octets. Une fois l’objet construit, l’appel `cin.`[tie](../standard-library/basic-ios-class.md#tie) retourne `&`[cout](#cout).

#### <a name="example"></a>Exemples

Dans cet exemple, `cin` définit le bit d’échec sur le flux de données lorsqu’il s’agit entre des caractères non numériques. Le programme efface le bit d’échec et supprime le caractère non valide à partir du flux pour continuer.

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

###  <a name="clog"></a> CLOG

Spécifie le flux global `clog`.

```cpp
extern ostream clog;
```

#### <a name="return-value"></a>Valeur de retour

Objet [ostream](../standard-library/ostream-typedefs.md#ostream).

#### <a name="remarks"></a>Notes

L’objet contrôle les insertions mises en mémoire tampon dans la sortie d’erreur standard sous forme de flux d’octets.

#### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `clog`, consultez [cerr](#cerr).

###  <a name="cout"></a> COUT

Spécifie le flux global `cout`.

```cpp
extern ostream cout;
```

#### <a name="return-value"></a>Valeur de retour

Objet [ostream](../standard-library/ostream-typedefs.md#ostream).

#### <a name="remarks"></a>Notes

L’objet contrôle les insertions dans la sortie standard sous forme de flux d’octets.

#### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `cout`, consultez [cerr](#cerr).

### <a name="wcerr"></a> wcerr

Spécifie le flux global `wcerr`.

```cpp
extern wostream wcerr;
```

#### <a name="return-value"></a>Valeur de retour

Objet [wostream](../standard-library/ostream-typedefs.md#wostream).

#### <a name="remarks"></a>Notes

L’objet contrôle les insertions non mises en mémoire tampon dans la sortie d’erreur standard sous forme de flux large. Une fois l’objet construit, l’expression `wcerr.`[flags](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) est différente de zéro.

#### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `wcerr`, consultez [cerr](#cerr).

### <a name="wcin"></a> wcin

Spécifie le flux global `wcin`.

```cpp
extern wistream wcin;
```

#### <a name="return-value"></a>Valeur de retour

Objet [wistream](../standard-library/istream-typedefs.md#wistream).

#### <a name="remarks"></a>Notes

L’objet contrôle les extractions à partir de l’entrée standard en tant que flux large. Une fois l’objet construit, l’appel `wcin.`[tie](../standard-library/basic-ios-class.md#tie) retourne `&`[wcout](#wcout).

#### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `wcin`, consultez [cerr](#cerr).

### <a name="wclog"></a> wclog

Spécifie le flux global `wclog`.

```cpp
extern wostream wclog;
```

#### <a name="return-value"></a>Valeur de retour

Objet [wostream](../standard-library/ostream-typedefs.md#wostream).

#### <a name="remarks"></a>Notes

L’objet contrôle les insertions mises en mémoire tampon dans la sortie d’erreur standard sous forme de flux large.

#### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `wclog`, consultez [cerr](#cerr).

### <a name="wcout"></a> wcout

Spécifie le flux global `wcout`.

```cpp
extern wostream wcout;
```

#### <a name="return-value"></a>Valeur de retour

Objet [wostream](../standard-library/ostream-typedefs.md#wostream).

#### <a name="remarks"></a>Notes

L'objet contrôle les insertions dans la sortie standard sous forme de flux large.

#### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `wcout`, consultez [cerr](#cerr).

Les instances de `CString` dans une instruction `wcout` doivent être converties en `const wchar_t*`, comme illustré dans l'exemple suivant.

```
CString cs("meow");

wcout <<(const wchar_t*) cs <<endl;
```

Pour plus d’informations, consultez [Opérations CString de base](../atl-mfc-shared/basic-cstring-operations.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programmation](../standard-library/iostream-programming.md)<br/>
[iostreams, conventions](../standard-library/iostreams-conventions.md)<br/>
