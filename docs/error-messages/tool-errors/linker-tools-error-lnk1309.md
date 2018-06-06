---
title: Erreur LNK1309 des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1309
dev_langs:
- C++
helpviewer_keywords:
- LNK1309
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ffecdc891a9fe0d1c17d6e36c87f5df10b449ec
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704096"
---
# <a name="linker-tools-error-lnk1309"></a>Erreur des outils Éditeur de liens LNK1309

> *type1* module détecté ; non valide avec commutateur CLRIMAGETYPE :*type2*

## <a name="remarks"></a>Notes

Un type d’image CLR a été demandé avec **CLRIMAGETYPE** , mais l’éditeur de liens n’a pas pu produire une image de ce type, car un ou plusieurs modules sont incompatibles avec ce type.

Par exemple, l’erreur LNK1309 s’affiche si vous spécifiez **/CLRIMAGETYPE:safe** et que vous passez un module généré avec **/CLR : pure**.

Le **/CLR : pure** et **/CLR : safe** les bibliothèques de prise en charge et les options du compilateur sont déconseillés dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

Vous verrez également LNK1309 si vous essayez de générer une application pure CLR de confiance partiel à l’aide de ptrustu [d] .lib. Pour plus d’informations sur la création d’une application de confiance partielle, consultez [Comment : créer une Application partiellement approuvée en supprimant la dépendance sur la DLL de la bibliothèque CRT](../../dotnet/create-a-partially-trusted-application.md).

Pour plus d’informations, consultez [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) et [/CLRIMAGETYPE (spécifier Type of CLR Image)](../../build/reference/clrimagetype-specify-type-of-clr-image.md).