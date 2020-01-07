---
title: C++arrêt du programme
ms.date: 12/10/2019
helpviewer_keywords:
- terminating execution
- quitting applications
- exiting applications
- programs [C++], terminating
ms.assetid: fa0ba9de-b5f1-4e7b-aa65-e7932068b48c
ms.openlocfilehash: a0e86cacd951327d39296a183be5ee4fbc36fd15
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301338"
---
# <a name="c-program-termination"></a>C++arrêt du programme

Dans C++, vous pouvez quitter un programme de l’une des manières suivantes :

- Appelez la fonction [Exit](exit-function.md) .
- Appelez la fonction [Abort](abort-function.md) .
- Exécutez une instruction [Return](return-statement-cpp.md) à partir de `main`.

## <a name="exit-function"></a>exit, fonction

La fonction [Exit](../c-runtime-library/reference/exit-exit-exit.md) , déclarée dans \<stdlib. h >, termine C++ un programme. La valeur fournie en tant qu’argument à `exit` est retournée au système d’exploitation en tant que code de retour ou code de sortie du programme. Par convention, un code de retour égal à zéro signifie que le programme s'est terminé correctement. Vous pouvez utiliser les constantes EXIT_FAILURE et EXIT_SUCCESS, également définies dans \<stdlib. h >, pour indiquer la réussite ou l’échec de votre programme.

L’émission d’une instruction **Return** à partir de la fonction `main` équivaut à appeler la fonction `exit` avec la valeur de retour comme argument.

## <a name="abort-function"></a>abort (fonction)

La fonction [Abort](../c-runtime-library/reference/abort.md) , également déclarée dans le fichier Include standard \<stdlib. h >, arrête C++ un programme. La différence entre les `exit` et les `abort` est que `exit` C++ autorise le traitement de l’arrêt au moment de l’exécution (les destructeurs d’objets globaux seront appelés), tandis que `abort` met immédiatement fin au programme. La fonction `abort` ignore le processus de destruction normal pour les objets statiques globaux initialisés. Il contourne également tout traitement spécial qui a été spécifié à l’aide de la fonction [atexit](../c-runtime-library/reference/atexit.md) .

## <a name="atexit-function"></a>atexit (fonction)

Utilisez la fonction [atexit](../c-runtime-library/reference/atexit.md) pour spécifier les actions qui s’exécutent avant l’arrêt du programme. Aucun objet statique global initialisé avant l’appel à **atexit** n’est détruit avant l’exécution de la fonction de traitement de sortie.

## <a name="return-statement-in-main"></a>instruction return dans main

L’émission d’une instruction [Return](return-statement-cpp.md) à partir de `main` est fonctionnellement équivalent à l’appel de la fonction `exit`. Prenons l'exemple suivant :

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

Les instructions `exit` et **Return** dans l’exemple précédent sont fonctionnellement identiques. Toutefois, C++ exige que les fonctions qui ont des types de retour autres que **void** retournent une valeur. L’instruction **Return** vous permet de retourner une valeur à partir de `main`.

## <a name="destruction-of-static-objects"></a>Destruction d’objets statiques

Lorsque vous appelez `exit` ou exécutez une instruction **Return** à partir d' `main`, les objets statiques sont détruits dans l’ordre inverse de leur initialisation (après l’appel à `atexit` le cas échéant). L'exemple suivant montre comment ce type d'initialisation et de nettoyage fonctionne.

### <a name="example"></a>Exemple

Dans l’exemple suivant, les objets statiques `sd1` et `sd2` sont créés et initialisés avant l’entrée dans `main`. Une fois que ce programme s’est arrêté à l’aide de l’instruction **Return** , la première `sd2` est détruite, puis `sd1`. Le destructeur de la classe `ShowData` ferme les fichiers associés à ces objets statiques.

```cpp
// using_exit_or_return1.cpp
#include <stdio.h>
class ShowData {
public:
   // Constructor opens a file.
   ShowData( const char *szDev ) {
   errno_t err;
      err = fopen_s(&OutputDev, szDev, "w" );
   }

   // Destructor closes the file.
   ~ShowData() { fclose( OutputDev ); }

   // Disp function shows a string on the output device.
   void Disp( char *szData ) {
      fputs( szData, OutputDev );
   }
private:
   FILE *OutputDev;
};

//  Define a static object of type ShowData. The output device
//   selected is "CON" -- the standard output device.
ShowData sd1 = "CON";

//  Define another static object of type ShowData. The output
//   is directed to a file called "HELLO.DAT"
ShowData sd2 = "hello.dat";

int main() {
   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

Une autre façon d’écrire ce code consiste à déclarer les objets `ShowData` avec portée de bloc, ce qui permet leur destruction lorsqu’ils sont hors de portée :

```cpp
int main() {
   ShowData sd1, sd2( "hello.dat" );

   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```


## <a name="see-also"></a>Voir aussi

[main : démarrage du programme](main-program-startup.md)