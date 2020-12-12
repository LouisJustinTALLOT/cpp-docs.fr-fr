---
description: 'En savoir plus sur : erreur du compilateur de ressources RW2001'
title: 'Erreur RW2001 du compilateur de ressources '
ms.date: 11/04/2016
f1_keywords:
- RW2001
helpviewer_keywords:
- RW2001
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
ms.openlocfilehash: e550854af4d504e484b722050f0274887956f2c6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337252"
---
# <a name="resource-compiler-error-rw2001"></a>Erreur RW2001 du compilateur de ressources 

Directive non valide dans le fichier RC prétraité

Le fichier RC contient une directive **#pragma** .

Utilisez la directive de préprocesseur **#ifndef** avec la constante **RC_INVOKED** que le compilateur de ressources définit lors du traitement d’un fichier include. Placez la directive **#pragma** à l’intérieur d’un bloc de code qui n’est pas traité lorsque la constante **RC_INVOKED** est définie. Le code dans le bloc est traité uniquement par le compilateur C/C++ et non par le compilateur de ressources. L’exemple de code suivant illustre cette technique :

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

La directive de préprocesseur **#pragma** n’a aucune signification dans un. Fichier RC. La directive de préprocesseur **#include** est fréquemment utilisée dans un. Fichier RC pour inclure un fichier d’en-tête (fichier d’en-tête personnalisé basé sur un projet ou un fichier d’en-tête standard fourni par Microsoft avec l’un de ses produits). Certains de ces fichiers include contiennent la directive **#pragma** . Comme un fichier d’en-tête peut inclure un ou plusieurs autres fichiers d’en-tête, le fichier qui contient la directive de **#pragma** incriminée peut ne pas être immédiatement évident.

La technique de **RC_INVOKED #ifndef** peut contrôler l’inclusion de fichiers d’en-tête dans des fichiers d’en-tête basés sur le projet.
