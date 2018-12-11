---
title: Avertissement de ligne de commande D9035
ms.date: 12/10/2018
f1_keywords:
- D9035
helpviewer_keywords:
- D9035
ms.assetid: 6254f933-e37a-45ba-b860-1a870d1bc8e8
ms.openlocfilehash: 9c0a159dcf193b4ad016069bafd86c557e9e1281
ms.sourcegitcommit: 6990f842fefc27b522b15cf352f3517b319d78da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248518"
---
# <a name="command-line-warning-d9035"></a>Avertissement de ligne de commande D9035

> option '*option*' a été déconseillée et sera supprimée dans une version ultérieure

## <a name="remarks"></a>Notes

Vous avez spécifié une option du compilateur qui sera supprimée dans une prochaine version du compilateur. S’il existe une suggestion de remplacement pour *option*, cet avertissement est suivi d’avertissement [D9036](../../error-messages/tool-errors/command-line-warning-d9036.md).

L’option spécifiée fonctionne toujours, mais vous devez mettre à jour votre configuration de build maintenant. Par conséquent, votre projet est plus probable continuer à créer lorsque vous mettez à niveau le compilateur.

## <a name="see-also"></a>Voir aussi

[Options du compilateur déconseillées et supprimées](../../build/reference/compiler-options-listed-by-category.md#deprecated-and-removed-compiler-options)<br/>
[Avertissement de ligne de commande D9036](command-line-warning-d9036.md)