---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4122'
title: Avertissement du compilateur (niveau 1) C4122
ms.date: 11/04/2016
f1_keywords:
- C4122
helpviewer_keywords:
- C4122
ms.assetid: 9a83eb0d-8708-42f7-988a-b0b6f2f646a0
ms.openlocfilehash: db8729d8822df5f71f08fcdecd5755b23adaa591
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155317"
---
# <a name="compiler-warning-level-1-c4122"></a>Avertissement du compilateur (niveau 1) C4122

'function' : alloc_text ne peut s’appliquer qu’aux fonctions avec liaison C

Le pragma **alloc_text** s’applique uniquement aux fonctions déclarées avec **extern c**. Il ne peut pas être utilisé avec des fonctions C++ externes.

Le pragma est ignoré.
