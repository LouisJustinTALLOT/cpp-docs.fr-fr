---
description: 'En savoir plus sur : utilisation de VERIFY au lieu d’Assert'
title: Utilisation de VERIFY au lieu d'ASSERT
ms.date: 05/06/2019
helpviewer_keywords:
- ASSERT statements
- debugging [MFC], ASSERT statements
- VERIFY macro
- assertions, troubleshooting ASSERT statements
- debugging assertions
- assertions, debugging
ms.assetid: 4c46397b-3fb1-49c1-a09b-41a72fae3797
ms.openlocfilehash: cbb878e9184536a6888b84f7861a3e8b7b9ab2b0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199049"
---
# <a name="using-verify-instead-of-assert"></a>Utilisation de VERIFY au lieu d'ASSERT

Supposons que lorsque vous exécutez la version Debug de votre application MFC, il n’y a aucun problème. Toutefois, la version finale de la même application se bloque, retourne des résultats incorrects et/ou présente un autre comportement anormal.

Ce problème peut survenir lorsque vous placez du code important dans une instruction Assert pour vérifier qu’il fonctionne correctement. Étant donné que les instructions Assert sont commentées dans une version Release d’un programme MFC, le code ne s’exécute pas dans une version Release.

Si vous utilisez Assert pour confirmer la réussite d’un appel de fonction, pensez à utiliser la méthode [verify](../mfc/reference/diagnostic-services.md#verify) à la place. La macro VERIFY évalue ses propres arguments à la fois dans les versions Debug et Release de l’application.

Une autre technique recommandée consiste à assigner la valeur de retour de la fonction à une variable temporaire, puis à tester la variable dans une instruction Assert.

Examinez le fragment de code suivant :

```
enum {
    sizeOfBuffer = 20
};
char *buf;
ASSERT(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

Ce code s’exécute parfaitement dans une version de débogage d’une application MFC. Si l’appel à `calloc( )` échoue, un message de diagnostic qui comprend le fichier et le numéro de ligne s’affiche. Toutefois, dans une version commerciale d’une application MFC :

- l’appel à `calloc( )` ne se produit jamais, en laissant `buf` non initialisé ou

- `strcpy_s( )` copie « `Hello, World` » dans une mémoire aléatoire, peut-être en cas de panne de l’application ou de blocage du système, ou

- `free()` tente de libérer de la mémoire qui n’a jamais été allouée.

Pour utiliser l’instruction Assert correctement, l’exemple de code doit être remplacé par ce qui suit :

```
enum {
    sizeOfBuffer = 20
};
char *buf;
buf = (char *) calloc(sizeOfBuffer, sizeof(char) );
ASSERT( buf != NULL );
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

Vous pouvez utiliser la vérification à la place :

```
enum {
    sizeOfBuffer = 20
};
char *buf;
VERIFY(buf = (char *) calloc(sizeOfBuffer, sizeof(char) ));
strcpy_s( buf, sizeOfBuffer, "Hello, World" );
free( buf );
```

## <a name="see-also"></a>Voir aussi

[Résolution des problèmes de version Release](fixing-release-build-problems.md)
