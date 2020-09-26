---
title: Arrêt du programme C++
description: Décrit les façons d' exit un programme en langage C++.
ms.date: 01/15/2020
helpviewer_keywords:
- terminating execution
- quitting applications
- exiting applications
- programs [C++], terminating
ms.assetid: fa0ba9de-b5f1-4e7b-aa65-e7932068b48c
no-loc:
- exit
- abort
- return
- main
- atexit
- void
ms.openlocfilehash: fd0c7699ae032b5551f4fbc37eb3b7fa999a168f
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352919"
---
# <a name="c-program-termination"></a>Arrêt du programme C++

En C++, vous pouvez exit un programme de l’une des manières suivantes :

- Appelez la [exit](../c-runtime-library/reference/exit-exit-exit.md) fonction.
- Appelez la [abort](../c-runtime-library/reference/abort.md) fonction.
- Exécutez une [return](return-statement-cpp.md) instruction à partir de `main` .

## <a name="no-locexit-function"></a>Fonction exit

La [exit](../c-runtime-library/reference/exit-exit-exit.md) fonction, déclarée dans \<stdlib.h> , met fin à un programme C++. La valeur fournie comme argument à `exit` est return Ed sur le système d’exploitation en tant que return code ou code du programme exit . Par Convention, un return Code de zéro signifie que le programme s’est terminé correctement. Vous pouvez utiliser les constantes EXIT_FAILURE et EXIT_SUCCESS, également définies dans \<stdlib.h> , pour indiquer la réussite ou l’échec de votre programme.

L’émission d’une **`return`** instruction à partir de la `main` fonction équivaut à appeler la `exit` fonction avec la return valeur comme argument.

## <a name="no-locabort-function"></a>Fonction abort

La [abort](../c-runtime-library/reference/abort.md) fonction, également déclarée dans le fichier Include standard \<stdlib.h> , met fin à un programme C++. La différence entre `exit` et `abort` est que `exit` permet au traitement de l’arrêt du runtime C++ d’avoir lieu (les destructeurs d’objets globaux sont appelés), tandis que `abort` met immédiatement fin au programme. La `abort` fonction ignore le processus de destruction normal pour les objets statiques globaux initialisés. Il contourne également tout traitement spécial qui a été spécifié à l’aide de la [atexit](../c-runtime-library/reference/atexit.md) fonction.

## <a name="no-locatexit-function"></a>Fonction atexit

Utilisez la [atexit](../c-runtime-library/reference/atexit.md) fonction pour spécifier les actions qui s’exécutent avant l’arrêt du programme. Aucun objet statique global initialisé avant l’appel à **atexit** n’est détruit avant l’exécution de la exit fonction de traitement.

## <a name="no-locreturn-statement-in-no-locmain"></a>return instruction dans main

L’émission d’une [return](return-statement-cpp.md) instruction à partir de `main` est fonctionnellement équivalente à l’appel de la `exit` fonction. Prenons l’exemple suivant :

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

Les `exit` **`return`** instructions et dans l’exemple précédent sont fonctionnellement identiques. Toutefois, C++ requiert que les fonctions qui ont des return types autres qu' **`void`** return une valeur. L' **`return`** instruction vous permet d' return obtenir une valeur à partir de `main` .

## <a name="destruction-of-static-objects"></a>Destruction d’objets statiques

Quand vous appelez `exit` ou exécutez une **`return`** instruction à partir de `main` , les objets statiques sont détruits dans l’ordre inverse de leur initialisation (après l’appel à s’il en `atexit` existe un). L'exemple suivant montre comment ce type d'initialisation et de nettoyage fonctionne.

### <a name="example"></a> Exemple

Dans l’exemple suivant, les objets statiques `sd1` et `sd2` sont créés et initialisés avant l’entrée dans `main` . Une fois que ce programme s’est arrêté à l’aide de l' **`return`** instruction, le premier `sd2` est détruit, puis `sd1` . Le destructeur de la classe `ShowData` ferme les fichiers associés à ces objets statiques.

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

[main arguments de ligne de commande et de fonction](main-function-command-line-args.md)
