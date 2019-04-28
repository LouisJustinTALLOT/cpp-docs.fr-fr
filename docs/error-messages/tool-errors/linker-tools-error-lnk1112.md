---
title: Erreur des outils Éditeur de liens LNK1112
ms.date: 11/04/2016
f1_keywords:
- LNK1112
helpviewer_keywords:
- LNK1112
ms.assetid: 425793d8-37e6-4072-9b6e-c3d4e9c12562
ms.openlocfilehash: bc01d56fb8144d23b91c82a7f791a70a5dadb7ef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62255468"
---
# <a name="linker-tools-error-lnk1112"></a>Erreur des outils Éditeur de liens LNK1112

> type d’ordinateur module '*type1*'est en conflit avec le type de machine cible'*type2*'

## <a name="remarks"></a>Notes

Les fichiers objets spécifiés en entrée ont été compilés pour différents types d’ordinateurs.

Par exemple, si vous essayez de lier un fichier objet compilé avec **/clr** et un fichier objet compilé avec **/clr:pure** (type d’ordinateur CEE), l’éditeur de liens génère l’erreur LNK1112. Le **/CLR : pure** option du compilateur est déconseillée dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

De même, si vous créez un module avec le x64 compilateur et un autre module avec le x86 compilateur et essayez de les lier, l’éditeur de liens génère l’erreur LNK1112.

Une raison possible de cette erreur est que vous développez une application 64 bits, mais que vous n’avez pas installé un des compilateurs 64 bits de Visual C++. Dans ce cas, les configurations 64 bits ne sont pas disponibles. Pour résoudre ce problème, exécutez le programme d’installation pour Visual Studio et installez les composants C++ manquants.

Cette erreur peut également se produire si vous modifiez la **configuration de la solution active** dans **Configuration Manager** , puis que vous tentez de générer le projet avant de supprimer les fichiers projet intermédiaires. Pour résoudre cette erreur, sélectionnez **Régénérer la Solution** dans le menu **Générer** . Vous pouvez aussi sélectionner **Nettoyer la solution** dans le **Générer** , puis générer la solution.

## <a name="see-also"></a>Voir aussi

- [Erreurs et avertissements des outils Éditeur de liens](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
