---
title: . CODE | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .CODE
dev_langs:
- C++
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff2d66cfc79e84c8c4c7cf92e117c9ac8c84a555
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43682485"
---
# <a name="code"></a>.CODE

Lorsqu’il est utilisé avec [. MODÈLE](../../assembler/masm/dot-model.md), indique le début d’un segment de code.

## <a name="syntax"></a>Syntaxe

> . CODE [[nom]]

#### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`name`|Paramètre facultatif qui spécifie le nom du segment de code. Le nom par défaut est _TEXT pour petite, petite, compact et plat [modèles](../../assembler/masm/dot-model.md). Le nom par défaut est *modulename*_TEXT pour d’autres modèles.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>
[.DATA](../../assembler/masm/dot-data.md)<br/>