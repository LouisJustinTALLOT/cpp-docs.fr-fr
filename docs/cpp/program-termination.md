---
title: Arrêt du programme C++
description: "Décrit les façons d' :::no-loc(exit)::: un programme en langage C++."
ms.date: 01/15/2020
helpviewer_keywords:
- terminating execution
- quitting applications
- :::no-loc(exit):::ing applications
- programs [C++], terminating
ms.assetid: fa0ba9de-b5f1-4e7b-aa65-e7932068b48c
no-loc:
- ':::no-loc(exit):::'
- ':::no-loc(abort):::'
- ':::no-loc(return):::'
- ':::no-loc(main):::'
- ':::no-loc(atexit):::'
- ':::no-loc(void):::'
ms.openlocfilehash: 216aef5dbe8d110f9d75d43b5009b89fc5bfda51
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227177"
---
# <a name="c-program-termination"></a>Arrêt du programme C++

En C++, vous pouvez :::no-loc(exit)::: un programme de l’une des manières suivantes :

- Appelez la [:::no-loc(exit):::](:::no-loc(exit):::-function.md) fonction.
- Appelez la [:::no-loc(abort):::](:::no-loc(abort):::-function.md) fonction.
- Exécutez une [:::no-loc(return):::](:::no-loc(return):::-statement-cpp.md) instruction à partir de `:::no-loc(main):::` .

## <a name="no-locexit-function"></a>Fonction :::no-loc(exit):::

La [:::no-loc(exit):::](../c-runtime-library/reference/:::no-loc(exit):::-:::no-loc(exit):::-:::no-loc(exit):::.md) fonction, déclarée dans \<stdlib.h> , met fin à un programme C++. La valeur fournie comme argument à `:::no-loc(exit):::` est :::no-loc(return)::: Ed sur le système d’exploitation en tant que :::no-loc(return)::: code ou code du programme :::no-loc(exit)::: . Par Convention, un :::no-loc(return)::: Code de zéro signifie que le programme s’est terminé correctement. Vous pouvez utiliser les constantes EXIT_FAILURE et EXIT_SUCCESS, également définies dans \<stdlib.h> , pour indiquer la réussite ou l’échec de votre programme.

L’émission d’une **`:::no-loc(return):::`** instruction à partir de la `:::no-loc(main):::` fonction équivaut à appeler la `:::no-loc(exit):::` fonction avec la :::no-loc(return)::: valeur comme argument.

## <a name="no-locabort-function"></a>Fonction :::no-loc(abort):::

La [:::no-loc(abort):::](../c-runtime-library/reference/:::no-loc(abort):::.md) fonction, également déclarée dans le fichier Include standard \<stdlib.h> , met fin à un programme C++. La différence entre `:::no-loc(exit):::` et `:::no-loc(abort):::` est que `:::no-loc(exit):::` permet au traitement de l’arrêt du runtime C++ d’avoir lieu (les destructeurs d’objets globaux sont appelés), tandis que `:::no-loc(abort):::` met immédiatement fin au programme. La `:::no-loc(abort):::` fonction ignore le processus de destruction normal pour les objets statiques globaux initialisés. Il contourne également tout traitement spécial qui a été spécifié à l’aide de la [:::no-loc(atexit):::](../c-runtime-library/reference/:::no-loc(atexit):::.md) fonction.

## <a name="no-locatexit-function"></a>Fonction :::no-loc(atexit):::

Utilisez la [:::no-loc(atexit):::](../c-runtime-library/reference/:::no-loc(atexit):::.md) fonction pour spécifier les actions qui s’exécutent avant l’arrêt du programme. Aucun objet statique global initialisé avant l’appel à **:::no-loc(atexit):::** n’est détruit avant l’exécution de la :::no-loc(exit)::: fonction de traitement.

## <a name="no-locreturn-statement-in-no-locmain"></a>:::no-loc(return):::instruction dans:::no-loc(main):::

L’émission d’une [:::no-loc(return):::](:::no-loc(return):::-statement-cpp.md) instruction à partir de `:::no-loc(main):::` est fonctionnellement équivalente à l’appel de la `:::no-loc(exit):::` fonction. Prenons l’exemple suivant :

```cpp
// :::no-loc(return):::_statement.cpp
#include <stdlib.h>
int :::no-loc(main):::()
{
    :::no-loc(exit):::( 3 );
    :::no-loc(return)::: 3;
}
```

Les `:::no-loc(exit):::` **`:::no-loc(return):::`** instructions et dans l’exemple précédent sont fonctionnellement identiques. Toutefois, C++ requiert que les fonctions qui ont des :::no-loc(return)::: types autres qu' **`:::no-loc(void):::`** :::no-loc(return)::: une valeur. L' **`:::no-loc(return):::`** instruction vous permet d' :::no-loc(return)::: obtenir une valeur à partir de `:::no-loc(main):::` .

## <a name="destruction-of-static-objects"></a>Destruction d’objets statiques

Quand vous appelez `:::no-loc(exit):::` ou exécutez une **`:::no-loc(return):::`** instruction à partir de `:::no-loc(main):::` , les objets statiques sont détruits dans l’ordre inverse de leur initialisation (après l’appel à s’il en `:::no-loc(atexit):::` existe un). L'exemple suivant montre comment ce type d'initialisation et de nettoyage fonctionne.

### <a name="example"></a>Exemple

Dans l’exemple suivant, les objets statiques `sd1` et `sd2` sont créés et initialisés avant l’entrée dans `:::no-loc(main):::` . Une fois que ce programme s’est arrêté à l’aide de l' **`:::no-loc(return):::`** instruction, le premier `sd2` est détruit, puis `sd1` . Le destructeur de la classe `ShowData` ferme les fichiers associés à ces objets statiques.

```cpp
// using_:::no-loc(exit):::_or_:::no-loc(return):::1.cpp
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
   :::no-loc(void)::: Disp( char *szData ) {
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

int :::no-loc(main):::() {
   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

Une autre façon d’écrire ce code consiste à déclarer les objets `ShowData` avec portée de bloc, ce qui permet leur destruction lorsqu’ils sont hors de portée :

```cpp
int :::no-loc(main):::() {
   ShowData sd1, sd2( "hello.dat" );

   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

## <a name="see-also"></a>Voir aussi

[:::no-loc(main):::arguments de ligne de commande et de fonction](:::no-loc(main):::-function-command-line-args.md)
