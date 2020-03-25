---
title: Avertissement RC4005 du compilateur de ressources
ms.date: 11/04/2016
f1_keywords:
- RC4005
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
ms.openlocfilehash: c428fefa90cceed6a8bc9b7f6e4b95ec2db5e039
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182407"
---
# <a name="resource-compiler-warning-rc4005"></a>Avertissement RC4005 du compilateur de ressources

'identificateur' : redéfinition de macro

L’identificateur est défini deux fois. Le compilateur a utilisé la deuxième définition de macro.

Cet avertissement peut être provoqué par la définition d’une macro sur la ligne de commande et dans le code à l’aide d’une directive `#define`. Cela peut également être dû à des macros importées à partir de fichiers include.

Pour éliminer l’avertissement, supprimez l’une des définitions ou utilisez une directive `#undef` avant la deuxième définition.
