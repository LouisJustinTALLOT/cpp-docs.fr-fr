---
title: ALIAS (MASM)
ms.date: 12/17/2019
f1_keywords:
- Alias
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
ms.openlocfilehash: 5aef169c5632e74722438c63718ce5b783a8da09
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316601"
---
# <a name="alias"></a>ALIAS

La directive d' **alias** crée un autre nom pour une fonction.  Cela vous permet de créer plusieurs noms pour une fonction, ou de créer des bibliothèques qui permettent à l’éditeur de liens (LINK. exe) de mapper une ancienne fonction à une nouvelle fonction.

## <a name="syntax"></a>Syntaxe

> **Alias \<** _alias_ **> = \<** _nom réel_ **>**

#### <a name="parameters"></a>Parameters

*nom réel*\
Nom réel de la fonction ou de la procédure.  Les chevrons sont requis.

*alias*\
Autre nom ou alias.  Les chevrons sont requis.

## <a name="see-also"></a>Voir aussi

Informations de référence sur les [Directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
