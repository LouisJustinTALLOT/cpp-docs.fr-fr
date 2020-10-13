---
title: Erreurs potentielles de passage d'objets CRT entre frontières DLL
description: Vue d’ensemble des problèmes potentiels que vous pouvez rencontrer lors du passage d’objets Microsoft C Runtime sur une limite de bibliothèque de liens dynamiques (DLL).
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DLL conflicts [C++]
ms.assetid: c217ffd2-5d9a-4678-a1df-62a637a96460
ms.openlocfilehash: 2d42803b5eca7a43f122d209b7d9e2d4e45c38de
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008933"
---
# <a name="potential-errors-passing-crt-objects-across-dll-boundaries"></a>Erreurs potentielles de passage d'objets CRT entre frontières DLL

Lorsque vous transmettez des objets Runtime C (CRT) tels que des descripteurs de fichiers, des paramètres régionaux et des variables d’environnement dans ou hors d’une DLL via des appels de fonction à travers la limite de DLL, un comportement inattendu peut se produire si la DLL ou tout fichier qui appelle la DLL utilise des copies différentes des bibliothèques CRT.

Un problème connexe peut se produire lorsque vous allouez de la mémoire (soit explicitement avec `new` ou `malloc` , soit implicitement avec `strdup` , `strstreambuf::str` , etc.), puis vous transmettez un pointeur sur une limite de dll où il est libéré. Cela peut entraîner une violation d’accès à la mémoire ou une altération du tas si la DLL et ses consommateurs utilisent des copies différentes des bibliothèques CRT.

Un autre symptôme de ce problème est une erreur dans la fenêtre de sortie pendant le débogage, par exemple `HEAP[]: Invalid Address specified to RtlValidateHeap(#,#)`

## <a name="causes"></a>Causes

Chaque copie de la bibliothèque CRT a un état séparé et distinct, conservé dans le stockage local de thread par votre application ou dans une DLL.

Les objets CRT tels que les descripteurs de fichiers, les variables d’environnement et les paramètres régionaux sont uniquement valides pour la copie de la bibliothèque CRT dans l’application ou la DLL où ces objets ont été alloués ou définis. Quand une DLL et ses clients utilisent des copies différentes de la bibliothèque CRT, vous ne pouvez pas passer ces objets CRT sur la limite de la DLL et vous attendre à ce qu’ils soient utilisés correctement de l’autre côté. Cela est vrai pour les versions CRT antérieures au CRT universel dans Visual Studio 2015 et versions ultérieures.

Dans Visual Studio 2013 et antérieur, chaque version de Visual Studio avait sa propre bibliothèque CRT. Les détails de l’implémentation interne de la bibliothèque CRT, tels que les structures de données et les conventions d’affectation des noms, étaient différents dans chaque version. La liaison dynamique du code qui a été compilé pour une version du CRT vers une autre version de la DLL CRT n’a jamais été prise en charge. Parfois, cela fonctionne, mais en raison de la chance plutôt que de la conception.

Étant donné que chaque copie de la bibliothèque CRT a son propre gestionnaire de tas, l’allocation de mémoire dans une bibliothèque CRT et le passage du pointeur sur une limite DLL à libérer par une autre copie de la bibliothèque CRT peuvent entraîner une altération du tas. Si vous concevez votre DLL de sorte qu’elle passe des objets CRT à travers la limite DLL, ou qu’elle alloue de la mémoire et s’attend à ce qu’elle soit libérée en dehors de la DLL, les clients de la DLL doivent utiliser la même copie de la bibliothèque CRT que la DLL.

La DLL et ses clients utilisent normalement la même copie de la bibliothèque CRT uniquement si, au moment du chargement, ils sont tous deux liés à la même version de la DLL CRT. Étant donné que la version DLL de la bibliothèque Universal CRT utilisée par Visual Studio 2015, et versions ultérieures sur Windows 10, est désormais un composant Windows déployé de manière centralisée (ucrtbase.dll), c’est le même pour les applications créées avec Visual Studio 2015 et versions ultérieures. Toutefois, même lorsque le code CRT est identique, vous ne pouvez pas attribuer la mémoire allouée dans un segment à un composant qui utilise un segment de mémoire différent.

## <a name="example-pass-file-handle-across-dll-boundary"></a>Exemple : passer le descripteur de fichier à travers la limite de DLL

### <a name="description"></a>Description

Cet exemple passe un handle de fichiers sur une limite DDL.

Les fichiers DLL et. exe sont générés avec `/MD` , afin qu’ils partagent une seule copie de la bibliothèque CRT.

Si vous régénérez avec `/MT` afin qu’ils utilisent des copies séparées du CRT, l’exécution du **test1Main.exe** résultant entraîne une violation d’accès.

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

## <a name="example-pass-environment-variables-across-dll-boundary"></a>Exemple : passer des variables d’environnement à travers les limites de DLL

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

Si la DLL et le fichier. exe sont générés avec `/MD` pour qu’une seule copie de la bibliothèque CRT soit utilisée, le programme s’exécute correctement et produit la sortie suivante :

```
New MYLIB variable is: c:\mylib;c:\yourlib
```

## <a name="see-also"></a>Voir aussi

[Fonctionnalités de la bibliothèque CRT](../c-runtime-library/crt-library-features.md)
