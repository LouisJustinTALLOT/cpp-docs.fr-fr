---
title: C.1 Notation | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a23b2631-8096-4bf3-ac23-ba4f4bd7a52a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4bbb3190dd5aa32315cd8f402f92fd94893b4b27
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411870"
---
# <a name="c1-notation"></a>C.1 Notation

Les règles de grammaire se composent du nom pour un non terminaux, suivie du signe deux-points, suivi d’alternatives de remplacement sur des lignes distinctes.

Le terme d’expression syntaxique<sub>opt</sub> indique que le terme est facultatif dans le remplacement.

L’expression syntaxique *terme*<sub>optseq</sub> équivaut à *terme-seq*<sub>opt</sub> avec les règles supplémentaires suivantes :

*terme-seq* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Terme*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*terme-seq* *terme*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*terme-seq* **,** *terme*