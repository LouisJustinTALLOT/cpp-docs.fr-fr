---
title: /CLRHEADER
ms.date: 11/04/2016
f1_keywords:
- /CLRHEADER
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
ms.openlocfilehash: 6a1240e2d3ad2ac3a454c610a6f49d07e50951e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272570"
---
# <a name="clrheader"></a>/CLRHEADER

Afficher les informations spécifiques au CLR.

## <a name="syntax"></a>Syntaxe

> /CLRHEADER *file*

### <a name="arguments"></a>Arguments

*fichier*<br/>
Un fichier image créé avec [/CLR](clr-common-language-runtime-compilation.md).

## <a name="remarks"></a>Notes

**/ /CLRHEADER** affiche des informations sur les en-têtes .NET utilisés dans n’importe quel programme géré. La sortie indique l’emplacement et la taille, en octets, de l’en-tête de .NET et les sections dans l’en-tête.

Uniquement les [/HEADERS](headers.md) (option DUMPBIN) est disponible pour les fichiers générés avec le [/GL](gl-whole-program-optimization.md) option du compilateur.

Lorsque **/CLRHEADER.** est utilisé sur un fichier qui a été compilé avec/CLR, il y aura un **clr Header :** section dans la sortie de dumpbin. La valeur de **indicateurs** indique l’option/CLR a été utilisée :

- 0--/clr (image peut contenir du code natif).

Vous pouvez également vérifier par programme si une image a été générée pour le common language runtime.  Pour plus d'informations, voir [Procédure : Déterminer si une Image est Native ou CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md).

Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017. Code qui doit être « pur » ou « sécurisée » doit être déplacée vers C#.

## <a name="see-also"></a>Voir aussi

- [DUMPBIN, options](dumpbin-options.md)
