---
title: Avertissement LNK4237 des outils Éditeur de liens | Microsoft Docs
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
ms.openlocfilehash: fcc109fe3ccf06e0461deed449517850271a2024
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39209389"
---
# <a name="linker-tools-warning-lnk4237"></a>Avertissement des outils Éditeur de liens LNK4237
/ SUBSYSTEM : native spécifié lors de l’importation à partir de 'dll' ; Utilisez/SUBSYSTEM : console ou/SUBSYSTEM : Windows.  
  
 [/ SUBSYSTEM : native](../../build/reference/subsystem-specify-subsystem.md) a été spécifié quand génération d’une application windows (Win32) qui utilise directement un ou plusieurs des opérations suivantes :  
  
-   kernel32.dll  
  
-   Gdi32.dll  
  
-   user32.dll  
  
-   un des fichier msvcrt\* DLL.  
  
 Résoudre cet avertissement en ne spécifiant ne pas **/SUBSYSTEM : native**.