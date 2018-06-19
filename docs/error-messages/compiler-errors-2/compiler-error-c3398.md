---
title: Erreur du compilateur C3398 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3398
dev_langs:
- C++
helpviewer_keywords:
- C3398
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b870479977bfb49ff39d5a15fe19fc700ed66b8e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33255828"
---
# <a name="compiler-error-c3398"></a>Erreur du compilateur C3398
'operator' : impossible de convertir de 'function_signature' en 'function_pointer'. L'expression source doit être un symbole de fonction  
  
 Quand la convention d’appel [__clrcall](../../cpp/clrcall.md) n’est pas spécifiée lors de la compilation avec **/clr**, le compilateur génère deux points d’entrée (adresses) pour chaque fonction : un point d’entrée natif et un point d’entrée managé.  
  
 Par défaut, le compilateur retourne le point d’entrée natif, mais dans certains cas, il est souhaitable d’avoir un point d’entrée managé (par exemple, lors de l’assignation de l’adresse à un pointeur de fonction `__clrcall` ). Pour que le compilateur puisse choisir de manière fiable le point d’entrée managé dans une assignation, le côté droit doit être un symbole de fonction.