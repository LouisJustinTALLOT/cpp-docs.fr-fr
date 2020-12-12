---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK1309'
title: Erreur des outils Éditeur de liens LNK1309
ms.date: 11/04/2016
f1_keywords:
- LNK1309
helpviewer_keywords:
- LNK1309
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
ms.openlocfilehash: e04498ae5226f748b6ba5cc2ce0cd9340f4547c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193641"
---
# <a name="linker-tools-error-lnk1309"></a>Erreur des outils Éditeur de liens LNK1309

> module *type1* détecté ; non valide avec le commutateur/CLRIMAGETYPE :*type2*

## <a name="remarks"></a>Notes

Un type d’image CLR a été demandé avec **/CLRIMAGETYPE** , mais l’éditeur de liens n’a pas pu produire une image de ce type, car un ou plusieurs modules étaient incompatibles avec ce type.

Par exemple, vous verrez LNK1309 si vous spécifiez **/CLRIMAGETYPE : safe** et que vous transmettez un module généré avec **/clr : pure**.

Les options de compilateur **/clr : pure** et **/clr : safe** et les bibliothèques de prise en charge sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017.

Vous verrez également LNK1309 si vous tentez de générer une application pure CLR partiellement approuvée à l’aide de ptrustu [d]. lib. Pour plus d’informations sur la création d’une application de niveau de confiance partielle, consultez Guide pratique [pour créer une application de confiance partielle en supprimant la dépendance sur la dll de bibliothèque CRT](../../dotnet/create-a-partially-trusted-application.md).

Pour plus d’informations, consultez [/clr (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) et [/CLRIMAGETYPE (spécifier le type d’image CLR)](../../build/reference/clrimagetype-specify-type-of-clr-image.md).
