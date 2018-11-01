---
title: C.1 Notation
ms.date: 11/04/2016
ms.assetid: a23b2631-8096-4bf3-ac23-ba4f4bd7a52a
ms.openlocfilehash: 593450b6dd7dcb30adbf8546ad96ff716c6fbc1c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473981"
---
# <a name="c1-notation"></a>C.1 Notation

Les règles de grammaire se composent du nom pour un non terminaux, suivie du signe deux-points, suivi d’alternatives de remplacement sur des lignes distinctes.

Le terme d’expression syntaxique<sub>opt</sub> indique que le terme est facultatif dans le remplacement.

L’expression syntaxique *terme*<sub>optseq</sub> équivaut à *terme-seq*<sub>opt</sub> avec les règles supplémentaires suivantes :

*terme-seq* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Terme*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*terme-seq* *terme*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*terme-seq* **,** *terme*