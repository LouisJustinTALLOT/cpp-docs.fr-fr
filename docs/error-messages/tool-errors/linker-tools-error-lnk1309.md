---
title: Erreur des outils Éditeur de liens LNK1309
ms.date: 11/04/2016
f1_keywords:
- LNK1309
helpviewer_keywords:
- LNK1309
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
ms.openlocfilehash: ea675ca835dfc3fe4881e5fabbea746a4442b10a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187441"
---
# <a name="linker-tools-error-lnk1309"></a>Erreur des outils Éditeur de liens LNK1309

> *type1* module détecté ; non valide avec commutateur CLRIMAGETYPE :*type2*

## <a name="remarks"></a>Notes

Un type d’image CLR a été demandé avec **CLRIMAGETYPE** mais l’éditeur de liens n’a pas pu produire une image de ce type, car un ou plusieurs modules étaient incompatibles avec ce type.

Par exemple, l’erreur LNK1309 s’affiche si vous spécifiez **/CLRIMAGETYPE:safe** et que vous passez un module généré avec **/CLR : pure**.

Le **/CLR : pure** et **/CLR : safe** les bibliothèques de prise en charge et les options du compilateur sont déconseillés dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

Vous verrez également LNK1309 si vous essayez de générer une application pure CLR de confiance partiel à l’aide de ptrustu [d] .lib. Pour plus d’informations sur la création d’une application partiellement approuvée, consultez [Comment : Créer une Application partiellement approuvée en supprimant la dépendance de la DLL de la bibliothèque CRT](../../dotnet/create-a-partially-trusted-application.md).

Pour plus d’informations, consultez [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) et [CLRIMAGETYPE (spécifier Type de CLR Image)](../../build/reference/clrimagetype-specify-type-of-clr-image.md).