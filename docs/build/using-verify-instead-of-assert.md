---
title: Utilisation de VERIFY au lieu d'ASSERT
ms.date: 11/04/2016
f1_keywords:
- assert
helpviewer_keywords:
- ASSERT statements
- debugging [MFC], ASSERT statements
- VERIFY macro
- assertions, troubleshooting ASSERT statements
- debugging assertions
- assertions, debugging
ms.assetid: 4c46397b-3fb1-49c1-a09b-41a72fae3797
ms.openlocfilehash: e6903616f8b4250b3d67db333be4fc17e8328952
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825281"
---
# <a name="using-verify-instead-of-assert"></a>Utilisation de VERIFY au lieu d'ASSERT

Supposons que lorsque vous exécutez la version debug de votre application MFC, il n’existe aucun problème. Toutefois, la version release de la même application se bloque, retourne des résultats incorrects et/ou présente certains autres comportement anormal.

Ce problème peut être provoqué lorsque vous placez le code important dans une instruction ASSERT pour vérifier qu’il effectue correctement. Étant donné que les instructions ASSERT sont commentées dans une version Release d’un programme MFC, le code ne s’exécute pas dans une version Release.

Si vous utilisez ASSERT pour confirmer qu’un appel de fonction a réussi, envisagez d’utiliser [Vérifiez](../mfc/reference/diagnostic-services.md#verify) à la place. La macro VERIFY évalue ses propres arguments dans les versions debug, et les versions release de l’application.

Une autre technique préférable consiste à affecter la valeur de retour de la fonction à une variable temporaire, puis tester la variable dans une instruction ASSERT.

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

Ce code s’exécute parfaitement dans une version debug d’une application MFC. Si l’appel à `calloc( )` échoue, un message qui inclut le nombre de lignes et les fichiers de diagnostic apparaît. Toutefois, dans une version commerciale d’une application MFC :

- l’appel à `calloc( )` ne se produit jamais, en laissant `buf` non initialisée, ou

- `strcpy_s( )` copies «`Hello, World`» dans une zone aléatoire de mémoire, bloquant probablement l’application ou à l’origine du système cesse de répondre, ou

- `free()` tente de libérer de la mémoire qui n’a jamais été allouée.

Pour utiliser ASSERT correctement, l’exemple de code doit être remplacé par les éléments suivants :

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

Ou bien, vous pouvez utiliser plutôt VERIFY :

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

[Résolution de problèmes liés à la version Release](fixing-release-build-problems.md)
