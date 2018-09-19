---
title: Erreur RW2001 du compilateur de ressources | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW2001
dev_langs:
- C++
helpviewer_keywords:
- RW2001
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f401ce7c9a96cfeecf195b8872a704b8b1291939
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114980"
---
# <a name="resource-compiler-error-rw2001"></a>Erreur RW2001 du compilateur de ressources 

Directive non valide dans le fichier RC prétraité

Le fichier RC contient un **#pragma** directive.

Utilisez le **#ifndef** directive de préprocesseur avec la **RC_INVOKED** constante que le compilateur de ressources définit quand il traite un fichier include. Place le **#pragma** directive à l’intérieur d’un bloc de code qui n’est pas traitée lorsque le **RC_INVOKED** constante n’est définie. Code dans le bloc est traité exclusivement par le compilateur C/C++ et non par le compilateur de ressources. L’exemple de code suivant illustre cette technique :

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

Le **#pragma** directive de préprocesseur n’a aucune signification un. Fichier RC. Le **#include** directive de préprocesseur est fréquemment utilisée dans un. Fichier RC pour inclure un fichier d’en-tête (un fichier de projet-en-tête personnalisé ou un fichier d’en-tête standard fourni par Microsoft avec l’un de ses produits). Certains de ces fichiers include contiennent la **#pragma** directive. Un fichier d’en-tête peut contenir un ou plusieurs autres fichiers d’en-tête, le fichier qui contient l’incriminé **#pragma** directive n’est pas forcément immédiatement évidente.

Le **#ifndef RC_INVOKED** technique peut contrôler, y compris les fichiers d’en-tête dans les fichiers d’en-tête de projet.