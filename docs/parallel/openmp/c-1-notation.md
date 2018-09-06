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
ms.openlocfilehash: 3d3ada700955c3acd2e96aa3e8a98c25c51393c1
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43766150"
---
# <a name="c1-notation"></a>C.1 Notation
Les règles de grammaire se composent du nom pour un non terminaux, suivie du signe deux-points, suivi d’alternatives de remplacement sur des lignes distinctes.

Le terme d’expression syntaxique<sub>opt</sub> indique que le terme est facultatif dans le remplacement.

L’expression syntaxique *terme*<sub>optseq</sub> équivaut à *terme-seq*<sub>opt</sub> avec les règles supplémentaires suivantes :

*terme-seq* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Terme*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*terme-seq* *terme*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*terme-seq* **,** *terme*