---
title: LNK4001 d’avertissement des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4001
dev_langs:
- C++
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: acf65c00c5c039769a05e009dcfe46ea42633ac4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300356"
---
# <a name="linker-tools-warning-lnk4001"></a>Avertissement des outils Éditeur de liens LNK4001
Aucun fichier objet spécifié ; bibliothèques utilisées  
  
 L’éditeur de liens a été passé à un ou plusieurs fichiers .lib, mais aucun fichier .obj.  
  
 Étant donné que l’éditeur de liens n’est pas en mesure d’accéder aux informations dans un fichier .lib capable d’accéder à un fichier .obj, cet avertissement indique que vous devrez spécifier explicitement d’autres options de l’éditeur de liens. Par exemple, vous devrez peut-être spécifier le [/MACHINE](../../build/reference/machine-specify-target-platform.md), [/OUT](../../build/reference/out-output-file-name.md), ou [/ENTRY](../../build/reference/entry-entry-point-symbol.md) options.