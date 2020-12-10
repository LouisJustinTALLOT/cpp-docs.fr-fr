---
title: Arrêt du programme C++
description: Découvrez les méthodes standard pour quitter un programme en langage C++.
ms.date: 12/07/2020
helpviewer_keywords:
- terminating execution
- quitting applications
- exiting applications
- programs [C++], terminating
ms.openlocfilehash: 15d31d8d454f6ac90e012d35ef14e6d6e0a9e29a
ms.sourcegitcommit: 754df5278f795f661d4eeb0d4cacc908aa630159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96933207"
---
# <a name="c-program-termination"></a>Arrêt du programme C++

En C++, vous pouvez quitter un programme de l’une des manières suivantes :

- Appelez la [`exit`](../c-runtime-library/reference/exit-exit-exit.md) fonction.
- Appelez la [`abort`](../c-runtime-library/reference/abort.md) fonction.
- Exécutez une [`return`](return-statement-cpp.md) instruction à partir de `main` .

## <a name="exit-function"></a>Fonction `exit`

La [`exit`](../c-runtime-library/reference/exit-exit-exit.md) fonction, déclarée dans \<stdlib.h> , met fin à un programme C++. La valeur fournie comme argument à `exit` est retournée au système d’exploitation en tant que code de retour ou code de sortie du programme. Par convention, un code de retour égal à zéro signifie que le programme s'est terminé correctement. Vous pouvez utiliser les constantes `EXIT_FAILURE` et `EXIT_SUCCESS` , également définies dans \<stdlib.h> , pour indiquer la réussite ou l’échec de votre programme.

L’émission d’une **`return`** instruction à partir de la `main` fonction équivaut à appeler la `exit` fonction avec la valeur de retour comme argument.

## <a name="abort-function"></a>Fonction `abort`

La [`abort`](../c-runtime-library/reference/abort.md) fonction, également déclarée dans le fichier Include standard \<stdlib.h> , met fin à un programme C++. La différence entre `exit` et `abort` est que `exit` permet au traitement de l’arrêt du runtime C++ d’avoir lieu (les destructeurs d’objets globaux sont appelés), mais `abort` met immédiatement fin au programme. La `abort` fonction ignore le processus de destruction normal pour les objets statiques globaux initialisés. Il contourne également tout traitement spécial qui a été spécifié à l’aide de la [`atexit`](../c-runtime-library/reference/atexit.md) fonction.

## <a name="atexit-function"></a>Fonction `atexit`

Utilisez la [`atexit`](../c-runtime-library/reference/atexit.md) fonction pour spécifier les actions qui s’exécutent avant la fin du programme. Aucun objet statique global initialisé avant l’appel à `atexit` n’est détruit avant l’exécution de la fonction de traitement de sortie.

## <a name="return-statement-in-main"></a>`return` instruction dans `main`

L’émission d’une [`return`](return-statement-cpp.md) instruction à partir de `main` est fonctionnellement équivalente à l’appel de la `exit` fonction. Prenons l’exemple suivant :

```cpp
// return_statement.cpp
#include <stdlib.h>
int main()
{
    exit( 3 );
    return 3;
}
```

Les `exit` **`return`** instructions et dans l’exemple précédent sont fonctionnellement identiques. En règle générale, C++ exige que les fonctions qui ont des types de retour autres que **`void`** retournent une valeur. La `main` fonction est une exception. elle peut se terminer sans **`return`** instruction. Dans ce cas, elle retourne une valeur spécifique à l’implémentation pour le processus appelant. L' **`return`** instruction vous permet de spécifier une valeur de retour à partir de `main` .

## <a name="destruction-of-static-objects"></a>Destruction d’objets statiques

Quand vous appelez `exit` ou exécutez une **`return`** instruction à partir de `main` , les objets statiques sont détruits dans l’ordre inverse de leur initialisation (après l’appel à s’il en `atexit` existe un). L'exemple suivant montre comment ce type d'initialisation et de nettoyage fonctionne.

### <a name="example"></a>Exemple

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
   ShowData sd1( "CON" ), sd2( "hello.dat" );

   sd1.Disp( "hello to default device\n" );
   sd2.Disp( "hello to file hello.dat\n" );
}
```

## <a name="see-also"></a>Voir aussi

[`main` arguments de ligne de commande et de fonction](main-function-command-line-args.md)
