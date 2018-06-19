---
title: LNK1302 d’erreur des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1302
dev_langs:
- C++
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6aa84a411f91303c84acb44e2e6c0ab3d975e19f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299417"
---
# <a name="linker-tools-error-lnk1302"></a>Erreur des outils Éditeur de liens LNK1302
uniquement prise en charge de liaison de .netmodules sécurisés ; Impossible de lier le fichier .netmodule  
  
 Un fichier .netmodule (compilé avec **/LN**) a été passé à l’éditeur de liens dans un utilisateur tente d’appeler la liaison MSIL.  Un module C++ est valide pour la liaison MSIL s’il est compilé avec **/CLR : safe**.  
  
 Pour corriger cette erreur, compilez avec **/CLR : safe** afin d’activer la liaison MSIL ou passez le **/CLR** ou **/CLR : pure** fichier .obj afin de l’éditeur de liens au lieu du module.  
  
 Pour plus d'informations, consultez  
  
-   [/LN (Créer le module MSIL)](../../build/reference/ln-create-msil-module.md)  
  
-   [Fichiers .netmodule en tant qu’entrée de l’Éditeur de liens](../../build/reference/netmodule-files-as-linker-input.md)