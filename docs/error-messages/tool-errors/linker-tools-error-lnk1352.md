---
title: Erreur des outils Éditeur de liens LNK1352
description: Erreur des outils Éditeur de liens LNK1352 se produit lors d’une tentative de fusion de section non prise en charge.
ms.date: 09/10/2019
f1_keywords:
- LNK1352
helpviewer_keywords:
- LNK1352
ms.openlocfilehash: 38f773bfd669529dfb1ada9c7bb59e6f0962c9c7
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908381"
---
# <a name="linker-tools-error-lnk1352"></a>Erreur des outils Éditeur de liens LNK1352

> '*section_name_1*'et'*section_name_2*'ne peuvent pas être fusionnés dans différentes sections

## <a name="remarks"></a>Notes

L’éditeur de liens a détecté une fusion de section qui n’est pas autorisée, car *section_name_1* et *section_name_2* doivent être fusionnés dans la même section. Par exemple, cette erreur se produit si l’éditeur de liens détecte une tentative de fusion `.stls` de la section `.tls` et de la section dans différentes sections.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

Vérifiez l’option [/Merge](../../build/reference/merge-combine-sections.md) sur la ligne de commande de l’éditeur de liens pour ce problème.

## <a name="see-also"></a>Voir aussi

[Erreurs et avertissements des outils Éditeur de liens](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
