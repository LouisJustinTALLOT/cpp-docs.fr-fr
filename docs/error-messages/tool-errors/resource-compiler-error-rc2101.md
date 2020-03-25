---
title: Erreur RC2101 du compilateur de ressources
ms.date: 11/04/2016
f1_keywords:
- RC2101
helpviewer_keywords:
- RC2101
ms.assetid: 580f9d74-162f-41e9-9438-ddbe3457c359
ms.openlocfilehash: 3fb576758e447c54e4ddfe7ddb024a1fd35a65f2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191650"
---
# <a name="resource-compiler-error-rc2101"></a>Erreur RC2101 du compilateur de ressources

Directive non valide dans le fichier RC prétraité

Le fichier du compilateur de ressources contient une directive **#pragma** .

Utilisez la directive de préprocesseur **#ifndef** avec la constante RC_INVOKED que le compilateur de ressources définit lors du traitement d’un fichier include. Placez la directive **#pragma** à l’intérieur d’un bloc de code qui n’est pas traité lorsque la constante RC_INVOKED est définie. Le code dans le bloc est traité uniquement par le compilateurC++ C/et non par le compilateur de ressources. L’exemple de code suivant illustre cette technique :

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

La directive de préprocesseur **#pragma** n’a aucune signification dans un. Fichier RC. La directive de préprocesseur **#include** est fréquemment utilisée dans un. Fichier RC pour inclure un fichier d’en-tête (fichier d’en-tête personnalisé basé sur un projet ou un fichier d’en-tête standard fourni par Microsoft avec l’un de ses produits). Certains de ces fichiers include contiennent la directive **#pragma** . Comme un fichier d’en-tête peut inclure un ou plusieurs autres fichiers d’en-tête, le fichier qui contient la directive de **#pragma** incriminée peut ne pas être immédiatement évident.

La technique de RC_INVOKED **#ifndef** peut contrôler l’inclusion de fichiers d’en-tête dans des fichiers d’en-tête basés sur le projet.
