---
title: LNK2011 d’erreur des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2011
dev_langs:
- C++
helpviewer_keywords:
- LNK2011
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f60dce4cb260c670f5ee82aa88b9f106f3f14e2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300745"
---
# <a name="linker-tools-error-lnk2011"></a>Erreur des outils Éditeur de liens LNK2011
objet précompilé ne pas lié dans ; image ne peut pas s’exécuter  
  
 Si vous utilisez des en-têtes précompilés, LINK requiert que tous les fichiers objets créés avec des en-têtes précompilés soient liés. Si vous avez un fichier source que vous utilisez pour générer un en-tête précompilé à utiliser avec d’autres fichiers de code source, vous devez maintenant inclure le fichier objet créé avec l’en-tête précompilé.  
  
 Par exemple, si vous compilez un fichier appelé STUB.cpp pour créer un en-tête précompilé à utiliser avec d’autres fichiers de code source, vous devez lier avec stub.obj sous ou vous obtenez cette erreur. Dans les lignes de commande suivantes, la ligne est utilisé pour créer un en-tête précompilé, COMMON.pch, utilisé avec PROG1.cpp et PROG2.cpp dans les lignes deux et trois. Le fichier stub.cpp ne contient que `#include` lignes (le même `#include` lignes comme dans PROG1.cpp et PROG2.cpp) et est utilisée uniquement pour générer des en-têtes précompilés. Dans la dernière ligne stub.obj sous doivent être liées dans pour éviter LNK2011.  
  
```  
cl /c /Yccommon.h stub.cpp  
cl /c /Yucommon.h prog1.cpp  
cl /c /Yucommon.h prog2.cpp  
link /out:prog.exe stub.obj prog1.obj prog2.obj  
```