---
title: LNK2008 d’erreur des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2008
dev_langs:
- C++
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4ee6a8a4c4cc6d33f47d5335daa9fccd4e5fd99
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299563"
---
# <a name="linker-tools-error-lnk2008"></a>Erreur des outils Éditeur de liens LNK2008
Cible de correction n’est pas alignée 'nom_symbole'  
  
 LINK a trouvé une cible de correction dans votre fichier d’objet qui n’était pas correctement aligné.  
  
 Cette erreur peut résulter d’alignement de section personnalisé (par exemple, #pragma [pack](../../preprocessor/pack.md)), [aligner](../../cpp/align-cpp.md) modificateur, ou à l’aide de code en langage assembleur qui modifie l’alignement.  
  
 Si votre code n’utilise pas un des éléments ci-dessus, cela peut être dû par le compilateur.