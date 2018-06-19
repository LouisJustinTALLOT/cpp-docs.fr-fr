---
title: Erreur du compilateur C2857 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2857
dev_langs:
- C++
helpviewer_keywords:
- C2857
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4bb2ec5047646bea420bf109f18a72d87a8f7c44
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246345"
---
# <a name="compiler-error-c2857"></a>Erreur du compilateur C2857
' #include ' instruction spécifiée avec l’option de ligne de commande /YcNomFichier est introuvable dans le fichier source  
  
 Le [/Yc](../../build/reference/yc-create-precompiled-header-file.md) option spécifie le nom d’un fichier include qui n’est pas inclus dans le fichier source qui est compilé.  
  
 Cette erreur peut être provoquée par un `#include` instruction dans un bloc de compilation conditionnelle n’est pas compilé.