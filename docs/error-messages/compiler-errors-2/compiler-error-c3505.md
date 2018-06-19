---
title: Erreur du compilateur C3505 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3505
dev_langs:
- C++
helpviewer_keywords:
- C3505
ms.assetid: ed73c99e-93a1-4f3a-bac7-ba7ed5d836e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e0ea8edd3237db2085365450f43b4b955d36f33
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257654"
---
# <a name="compiler-error-c3505"></a>Erreur du compilateur C3505

> Impossible de charger la bibliothèque de type '*guid*'  
  
C3505 peut être provoquée si vous exécutez le compilateur d’entre 32 bits, x86 hébergés 64 bits, x64 cibles sur une version 64 bits de l’ordinateur, car le compilateur s’exécute sous WOW64 et ne peuvent lire à partir de la ruche du Registre 32 bits.  
  
Vous pouvez résoudre cette erreur en créant des versions 32 bits et 64 bits de la bibliothèque de types que vous essayez d’importer et ensuite enregistrer les deux.  Vous pouvez également utiliser le compilateur 64 bits natif, ce qui vous oblige à modifier votre **répertoires VC ++** propriété dans l’IDE pour pointer vers le compilateur 64 bits.  
  
Pour plus d'informations, consultez  
  
-   [Guide pratique pour activer un ensemble d’outils du compilateur Visual C++ 64 bits sur la ligne de commande](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)  
  
-   [Guide pratique pour configurer des projets Visual C++ pour cibler des plateformes x64 64 bits](../../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)