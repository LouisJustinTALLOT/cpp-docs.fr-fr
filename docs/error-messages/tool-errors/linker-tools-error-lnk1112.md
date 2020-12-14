---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK1112'
title: Erreur des outils Éditeur de liens LNK1112
ms.date: 11/04/2016
f1_keywords:
- LNK1112
helpviewer_keywords:
- LNK1112
ms.assetid: 425793d8-37e6-4072-9b6e-c3d4e9c12562
ms.openlocfilehash: ba0a34e07b0806f251c0b1237dc28ab5f8becbf4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281377"
---
# <a name="linker-tools-error-lnk1112"></a>Erreur des outils Éditeur de liens LNK1112

> le type d’ordinateur de module «*type1*» est en conflit avec le type d’ordinateur cible «*type2*»

## <a name="remarks"></a>Notes

Les fichiers objets spécifiés en entrée ont été compilés pour différents types d’ordinateurs.

Par exemple, si vous essayez de lier un fichier objet compilé avec **/clr** et un fichier objet compilé avec **/clr:pure** (type d’ordinateur CEE), l’éditeur de liens génère l’erreur LNK1112. L’option de compilateur **/clr : pure** est déconseillée dans visual studio 2015 et n’est pas prise en charge dans visual studio 2017.

De même, si vous créez un module avec le compilateur x64 et un autre module avec le compilateur x86, et que vous tentez de les lier, l’éditeur de liens génère l’LNK1112.

Une raison possible de cette erreur est que vous développez une application 64 bits, mais que vous n’avez pas installé un des compilateurs 64 bits de Visual C++. Dans ce cas, les configurations 64 bits ne sont pas disponibles. Pour résoudre ce problème, exécutez le programme d’installation pour Visual Studio et installez les composants C++ manquants.

Cette erreur peut également se produire si vous modifiez la **configuration de la solution active** dans **Configuration Manager** , puis que vous tentez de générer le projet avant de supprimer les fichiers projet intermédiaires. Pour résoudre cette erreur, sélectionnez **Régénérer la Solution** dans le menu **Générer** . Vous pouvez aussi sélectionner **Nettoyer la solution** dans le **Générer** , puis générer la solution.

## <a name="see-also"></a>Voir aussi

- [Erreurs et avertissements des outils Éditeur de liens](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
