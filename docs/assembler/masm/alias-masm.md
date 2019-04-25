---
title: ALIAS (MASM)
ms.date: 08/30/2018
f1_keywords:
- Alias
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
ms.openlocfilehash: ab00092f410d34119e876db4562e6d0709743d79
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166488"
---
# <a name="alias-masm"></a>ALIAS (MASM)

Le **ALIAS** directive crée un autre nom pour une fonction.  Cela vous permet de créer plusieurs noms pour une fonction, ou créer des bibliothèques qui permettent de l’éditeur de liens (LINK.exe) pour mapper une ancienne fonction vers une nouvelle fonction.

## <a name="syntax"></a>Syntaxe

> ALIAS \< *alias*> = \< *nom réel*>

#### <a name="parameters"></a>Paramètres

*actual-name*<br/>
Le nom réel de la fonction ou de la procédure.  Les crochets sont nécessaires.

*alias*<br/>
Le nom de remplacement ou l’alias.  Les crochets sont nécessaires.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>