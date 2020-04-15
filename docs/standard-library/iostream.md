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
ms.openlocfilehash: 03afb777dc3926284cf0dc625e94a716ecdf5413
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375342"
---
# <a name="ltiostreamgt"></a>&lt;iostream&gt;

Déclare des objets qui contrôlent la lecture et l'écriture des flux standard. Cela inclut est souvent le seul en-tête dont vous avez besoin pour faire l’entrée et la sortie d’un programme C .

## <a name="syntax"></a>Syntaxe

```cpp
#include <iostream>
```

> [!NOTE]
> La \<bibliothèque iostream> utilise `#include <ios>` `#include <streambuf>`le `#include <istream>`, `#include <ostream>` , , et les déclarations.

## <a name="remarks"></a>Notes

Les objets se répartissent en deux groupes :

- [cin](#cin), [cout](#cout), [cerr](#cerr), et [obstruer](#clog) sont orientés byte, faire des transferts d’au revoir conventionnels.

- [wcin](#wcin), [wcout](#wcout), [wcerr](#wcerr) et [wclog](#wclog) sont orientés largeur et traduisent vers et à partir des caractères larges que le programme manipule en interne.

Une fois que vous faites certaines opérations sur un flux, comme l’entrée standard, vous ne pouvez pas effectuer des opérations d’une orientation différente sur le même flux. Par conséquent, un programme ne peut pas fonctionner de façon interchangeable sur [cin](#cin) et [wcin](#wcin), par exemple.

Tous les objets déclarés dans cet en-tête partagent une propriété particulière — vous pouvez supposer \<qu’ils sont construits avant tout objet statique que vous définissez, dans une unité de traduction qui comprend des> iostream. De même, vous pouvez supposer que ces objets ne sont pas détruits avant les destructeurs pour de tels objets statiques que vous définissez. (Les flux de sortie sont toutefois rincés pendant la résiliation du programme.) Par conséquent, vous pouvez lire ou écrire en toute sécurité à partir ou écrire aux flux standard avant le démarrage du programme et après la fin du programme.

Cette garantie n’est cependant pas universelle. Un constructeur statique peut appeler une fonction dans une autre unité de traduction. La fonction appelée ne peut pas supposer que les objets déclarés dans cet en-tête ont été construits, étant donné l’ordre incertain dans lequel les unités de traduction participent à la construction statique. Pour utiliser ces objets dans ce contexte, vous devez d’abord construire un objet de classe [ios_base::Init](../standard-library/ios-base-class.md#init).

### <a name="global-stream-objects"></a>Objets de flux global

|||
|-|-|
|[cerr](#cerr)|Spécifie le flux global `cerr`.|
|[Cin](#cin)|Spécifie le flux global `cin`.|
|[Boucher](#clog)|Spécifie le flux global `clog`.|
|[cout](#cout)|Spécifie le flux global `cout`.|
|[wcerr](#wcerr)|Spécifie le flux global `wcerr`.|
|[wcin (wcin)](#wcin)|Spécifie le flux global `wcin`.|
|[wclog](#wclog)|Spécifie le flux global `wclog`.|
|[wcout](#wcout)|Spécifie le flux global `wcout`.|

### <a name="cerr"></a><a name="cerr"></a>cerr cerr

L’objet `cerr` contrôle la sortie vers une mémoire tampon de flux associée à l’objet `stderr`, déclaré dans \<cstdio>.

```cpp
extern ostream cerr;
```

#### <a name="return-value"></a>Valeur de retour

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

### <a name="cin"></a><a name="cin"></a>Cin

Spécifie le flux global `cin`.

```cpp
extern istream cin;
```

#### <a name="return-value"></a>Valeur de retour

Objet [istream](../standard-library/istream-typedefs.md#istream).

#### <a name="remarks"></a>Notes

L’objet contrôle les extractions à partir de l’entrée standard en tant que flux d’octets. Une fois l’objet construit, l’appel `cin.`[tie](../standard-library/basic-ios-class.md#tie) retourne `&`[cout](#cout).

#### <a name="example"></a>Exemple

Dans cet `cin` exemple, définit le bit d’échec sur le flux quand il tombe sur des caractères non numériques. Le programme efface le bit échec et dépouille le caractère invalide du flux pour continuer.

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

### <a name="clog"></a><a name="clog"></a>Boucher

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

### <a name="cout"></a><a name="cout"></a>cout (en)

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

### <a name="wcerr"></a><a name="wcerr"></a>wcerr wcerr

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

### <a name="wcin"></a><a name="wcin"></a>wcin (wcin)

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

### <a name="wclog"></a><a name="wclog"></a>wclog

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

### <a name="wcout"></a><a name="wcout"></a>wcout

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

```cpp
CString cs("meow");

wcout <<(const wchar_t*) cs <<endl;
```

Pour plus d’informations, consultez [Opérations CString de base](../atl-mfc-shared/basic-cstring-operations.md).

## <a name="see-also"></a>Voir aussi

[Référence de fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des fils dans la bibliothèque standard de CMD](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programmation iostream](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
