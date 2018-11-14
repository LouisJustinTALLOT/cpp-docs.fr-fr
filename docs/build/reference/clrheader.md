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
ms.openlocfilehash: e35cf79cdaa10c9632e1c588e2b49f45cfbef283
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330851"
---
# <a name="clrheader"></a>/CLRHEADER

Afficher les informations spécifiques au CLR.

## <a name="syntax"></a>Syntaxe

> / /CLRHEADER *fichier*

### <a name="arguments"></a>Arguments

*fichier*<br/>
Un fichier image créé avec [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="remarks"></a>Notes

**/ /CLRHEADER** affiche des informations sur les en-têtes .NET utilisés dans n’importe quel programme géré. La sortie indique l’emplacement et la taille, en octets, de l’en-tête de .NET et les sections dans l’en-tête.

Uniquement les [/HEADERS](../../build/reference/headers.md) (option DUMPBIN) est disponible pour les fichiers générés avec le [/GL](../../build/reference/gl-whole-program-optimization.md) option du compilateur.

Lorsque **/CLRHEADER.** est utilisé sur un fichier qui a été compilé avec/CLR, il y aura un **clr Header :** section dans la sortie de dumpbin. La valeur de **indicateurs** indique l’option/CLR a été utilisée :

- 0--/clr (image peut contenir du code natif).

Vous pouvez également vérifier par programme si une image a été générée pour le common language runtime.  Pour plus d’informations, consultez [Comment : déterminer si une Image est Native ou CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md).

Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017. Code qui doit être « pur » ou « sécurisée » doit être déplacée vers C#.

## <a name="see-also"></a>Voir aussi

- [DUMPBIN, options](../../build/reference/dumpbin-options.md)
