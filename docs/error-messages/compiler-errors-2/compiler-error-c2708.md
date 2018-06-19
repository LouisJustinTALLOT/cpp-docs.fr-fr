---
title: Erreur du compilateur C2708 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2708
dev_langs:
- C++
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d30b2e5c1856a604ae314316cd71d6acc00a7c74
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234758"
---
# <a name="compiler-error-c2708"></a>Erreur du compilateur C2708
'identificateur' : longueur en octets des paramètres réels diffère d’appel précédent ou référence  
  
 A [__stdcall](../../cpp/stdcall.md) fonction doit être précédée d’un prototype. Sinon, le compilateur interprète le premier appel à la fonction en tant que prototype et cette erreur se produit lorsque le compilateur rencontre un appel qui ne correspond pas.  
  
 Pour résoudre ce problème, ajoutez un prototype de fonction.