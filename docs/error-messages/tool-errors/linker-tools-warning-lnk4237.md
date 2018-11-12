---
title: Avertissement des outils Éditeur de liens LNK4237
ms.date: 11/04/2016
f1_keywords:
- LNK4237
helpviewer_keywords:
- LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
ms.openlocfilehash: 62ce0a0edc7f15bc5a19e4630133976f413da35a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588615"
---
# <a name="linker-tools-warning-lnk4237"></a>Avertissement des outils Éditeur de liens LNK4237

/ SUBSYSTEM : native spécifié lors de l’importation à partir de 'dll' ; Utilisez/SUBSYSTEM : console ou/SUBSYSTEM : Windows.

[/ SUBSYSTEM : native](../../build/reference/subsystem-specify-subsystem.md) a été spécifié quand génération d’une application windows (Win32) qui utilise directement un ou plusieurs des opérations suivantes :

- kernel32.dll

- Gdi32.dll

- user32.dll

- un des fichier msvcrt\* DLL.

Résoudre cet avertissement en ne spécifiant ne pas **/SUBSYSTEM : native**.