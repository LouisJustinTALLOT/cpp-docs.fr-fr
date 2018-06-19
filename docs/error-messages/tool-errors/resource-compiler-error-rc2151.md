---
title: Erreur RC2151 du compilateur de ressources | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2151
dev_langs:
- C++
helpviewer_keywords:
- RC2151
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8349aa14de6aec96fa1b526cbcffbe79036f804d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323470"
---
# <a name="resource-compiler-error-rc2151"></a>Erreur RC2151 du compilateur de ressources 
Impossible de réutiliser les constantes de chaîne  
  
 À l’aide de la même valeur à deux reprises dans un **STRINGTABLE** instruction. Assurez-vous que vous n’utilisez pas plusieurs chevauchement des valeurs décimales et hexadécimales.  
  
 Chaque ID d’une **STRINGTABLE** doit être unique. Pour une efficacité maximale utilisez des constantes contiguës commençant par un multiple de 16.