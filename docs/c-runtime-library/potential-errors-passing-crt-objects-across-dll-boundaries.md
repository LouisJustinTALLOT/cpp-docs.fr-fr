---
title: Erreurs potentielles de passage d'objets CRT entre frontières DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DLL conflicts [C++]
ms.assetid: c217ffd2-5d9a-4678-a1df-62a637a96460
ms.openlocfilehash: 31f9d9aceba167b516c9d37724e240f1bc4586e1
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749896"
---
# <a name="potential-errors-passing-crt-objects-across-dll-boundaries"></a>Erreurs potentielles de passage d'objets CRT entre frontières DLL

Lorsque vous passez des objets CRT tels que des handles de fichiers, des paramètres régionaux et des variables d'environnement dans ou hors d'une DDL (appels de fonction sur la limite DDL), un comportement inattendu peut se produire si la DDL, ainsi que les fichiers qui l'appellent, utilisent des copies différentes des librairies CRT.

Un problème connexe peut se produire lorsque vous allouez de la mémoire (soit explicitement avec `new` ou `malloc`, soit implicitement avec `strdup`, `strstreambuf::str`, etc.), puis passez un pointeur sur une limite DLL à libérer. Cela peut entraîner une violation d'accès à la mémoire ou une altération du tas si la DLL et ses utilisateurs utilisent des copies différentes des bibliothèques CRT.

Un autre symptôme de ce problème peut être une erreur dans la fenêtre de sortie pendant le débogage, notamment :

HEAP[] : adresse non valide spécifiée dans RtlValidateHeap(#,#)

## <a name="causes"></a>Causes

Chaque copie de la bibliothèque CRT a un état séparé et distinct, conservé dans le stockage local de thread par votre application ou dans une DLL. Ainsi, les objets CRT comme les descripteurs de fichiers, les variables d’environnement et les paramètres régionaux sont uniquement valides pour la copie de la bibliothèque CRT dans l’application ou la DLL dans laquelle ces objets sont alloués ou définis. Quand une DLL et ses clients d’application utilisent des copies différentes de la bibliothèque CRT, vous ne pouvez pas passer ces objets CRT sur la limite DLL et vous attendre à ce qu’ils soient récupérés correctement en sortie. Cela est particulièrement vrai pour les versions CRT antérieures au CRT universel dans Visual Studio 2015 et versions ultérieures. Une version spécifique de la bibliothèque CRT correspond à chaque version de Visual Studio créée avec Visual C++ 2013 ou version antérieure. Les détails de l’implémentation interne du CRT, par exemple, ses structures de données et les conventions de nommage, sont différents dans chaque version. La liaison dynamique du code compilé pour une version du CRT avec une version différente de la DLL CRT n’a jamais été prise en charge, bien qu’elle ait des chances de fonctionner (du fait du hasard et non de sa conception).

En outre, étant donné que chaque copie de la bibliothèque CRT a son propre gestionnaire de tas, l'allocation de mémoire dans une bibliothèque CRT et le passage du pointeur sur une limite DLL à libérer par une autre copie de la bibliothèque CRT est une cause potentielle d'altération du tas. Si vous concevez votre DLL de sorte qu’elle passe des objets CRT sur la limite ou alloue de la mémoire, et souhaitez qu’elle soit libérée en dehors de la DLL, vous obligez les clients d’application de la DLL à utiliser la même copie de la bibliothèque CRT que la DLL. La DLL et ses clients utilisent normalement la même copie de la bibliothèque CRT uniquement si, au moment du chargement, ils sont tous deux liés à la même version de la DLL CRT. Comme la version DLL de la bibliothèque CRT universelle utilisée par Visual Studio 2015 et version ultérieure sur Windows 10 est désormais un composant Windows déployé de manière centralisée (ucrtbase.dll), il est identique pour les applications créées avec Visual Studio 2015 et versions ultérieures. Toutefois, même quand le code CRT est identique, vous ne pouvez pas transférer la mémoire allouée d’un tas vers un composant qui utilise un autre tas.

## <a name="example"></a>Exemple

### <a name="description"></a>Description

Cet exemple passe un handle de fichiers sur une limite DDL.

La DLL et le fichier .exe sont générés avec /MD de sorte qu'ils partagent une seule copie de la bibliothèque CRT.

Si vous les régénérez avec /MT de sorte qu'ils utilisent des copies distinctes de la bibliothèque CRT, l'exécution du fichier test1Main.exe résultant provoque une violation d'accès.

```cpp
// test1Dll.cpp
// compile with: cl /EHsc /W4 /MD /LD test1Dll.cpp
#include <stdio.h>
__declspec(dllexport) void writeFile(FILE *stream)
{
   char   s[] = "this is a string\n";
   fprintf( stream, "%s", s );
   fclose( stream );
}
```

```cpp
// test1Main.cpp
// compile with: cl /EHsc /W4 /MD test1Main.cpp test1Dll.lib
#include <stdio.h>
#include <process.h>
void writeFile(FILE *stream);

int main(void)
{
   FILE  * stream;
   errno_t err = fopen_s( &stream, "fprintf.out", "w" );
   writeFile(stream);
   system( "type fprintf.out" );
}
```

```Output
this is a string
```

## <a name="example"></a>Exemple

### <a name="description"></a>Description

Cet exemple passe des variables d'environnement sur une limite DDL.

```cpp
// test2Dll.cpp
// compile with: cl /EHsc /W4 /MT /LD test2Dll.cpp
#include <stdio.h>
#include <stdlib.h>

__declspec(dllexport) void readEnv()
{
   char *libvar;
   size_t libvarsize;

   /* Get the value of the MYLIB environment variable. */
   _dupenv_s( &libvar, &libvarsize, "MYLIB" );

   if( libvar != NULL )
      printf( "New MYLIB variable is: %s\n", libvar);
   else
      printf( "MYLIB has not been set.\n");
   free( libvar );
}
```

```cpp
// test2Main.cpp
// compile with: cl /EHsc /W4 /MT test2Main.cpp test2dll.lib
#include <stdlib.h>
#include <stdio.h>

void readEnv();

int main( void )
{
   _putenv( "MYLIB=c:\\mylib;c:\\yourlib" );
   readEnv();
}
```

```Output
MYLIB has not been set.
```

Si la DLL et le fichier .exe sont générés tous les deux avec /MD de sorte qu'une seule copie de la bibliothèque CRT soit utilisée, le programme s'exécute correctement et produit la sortie suivante :

```
New MYLIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>Voir aussi

[Fonctionnalités de bibliothèque CRT](../c-runtime-library/crt-library-features.md)
