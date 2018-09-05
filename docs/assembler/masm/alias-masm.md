---
title: ALIAS (MASM) | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Alias
dev_langs:
- C++
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6a977d35040d8ca25cd3bd4ae4def233092b37a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691060"
---
# <a name="alias-masm"></a>ALIAS (MASM)

Le **ALIAS** directive crée un autre nom pour une fonction.  Cela vous permet de créer plusieurs noms pour une fonction, ou créer des bibliothèques qui permettent de l’éditeur de liens (LINK.exe) pour mapper une ancienne fonction vers une nouvelle fonction.

## <a name="syntax"></a>Syntaxe

> ALIAS \< *alias*> = \< *nom réel*>

#### <a name="parameters"></a>Paramètres

*nom réel*<br/>
Le nom réel de la fonction ou de la procédure.  Les crochets sont nécessaires.

*alias*<br/>
Le nom de remplacement ou l’alias.  Les crochets sont nécessaires.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>