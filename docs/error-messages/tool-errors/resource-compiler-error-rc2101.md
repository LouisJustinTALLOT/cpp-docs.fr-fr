---
title: 'Erreur RC2101 du compilateur de ressources '
ms.date: 11/04/2016
f1_keywords:
- RC2101
helpviewer_keywords:
- RC2101
ms.assetid: 580f9d74-162f-41e9-9438-ddbe3457c359
ms.openlocfilehash: 595e87b73d79a01993e0e9b3aaa814332b21413f
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345285"
---
# <a name="resource-compiler-error-rc2101"></a>Erreur RC2101 du compilateur de ressources 

Directive non valide dans le fichier RC prétraité

Le fichier du compilateur de ressources contient un **#pragma** directive.

Utilisez le **#ifndef** directive de préprocesseur avec la constante RC_INVOKED définie par le compilateur de ressources lorsqu’il traite un fichier include. Place le **#pragma** directive à l’intérieur d’un bloc de code qui n’est pas traité lorsque la constante RC_INVOKED est définie. Code dans le bloc est traité exclusivement par le compilateur C/C++ et non par le compilateur de ressources. L’exemple de code suivant illustre cette technique :

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

Le **#pragma** directive de préprocesseur n’a aucune signification un. Fichier RC. Le **#include** directive de préprocesseur est fréquemment utilisée dans un. Fichier RC pour inclure un fichier d’en-tête (un fichier de projet-en-tête personnalisé ou un fichier d’en-tête standard fourni par Microsoft avec l’un de ses produits). Certains de ces fichiers include contiennent la **#pragma** directive. Un fichier d’en-tête peut contenir un ou plusieurs autres fichiers d’en-tête, le fichier qui contient l’incriminé **#pragma** directive n’est pas forcément immédiatement évidente.

Le **#ifndef** RC_INVOKED peut contrôler, y compris les fichiers d’en-tête dans les fichiers d’en-tête de projet.