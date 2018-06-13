---
title: LNK4237 d’avertissement des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4237
dev_langs:
- C++
helpviewer_keywords:
- LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5acccf52d3738985c7a83432342952af03bf78b4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302865"
---
# <a name="linker-tools-warning-lnk4237"></a>Avertissement des outils Éditeur de liens LNK4237
/ SUBSYSTEM : native spécifié lors de l’importation à partir de 'dll' ; Utilisez/SUBSYSTEM : console ou/SUBSYSTEM : Windows.  
  
 [/ SUBSYSTEM : native](../../build/reference/subsystem-specify-subsystem.md) a été spécifié quand génération d’une application windows (Win32) qui utilise directement un ou plusieurs des opérations suivantes :  
  
-   kernel32.dll  
  
-   Gdi32.dll  
  
-   user32.dll  
  
-   une des DLL msvcrt *.  
  
 Résoudre cet avertissement en ne spécifiant **/SUBSYSTEM : native**.