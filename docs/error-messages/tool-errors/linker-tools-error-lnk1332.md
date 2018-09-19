---
title: Erreur des LNK1332 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1332
dev_langs:
- C++
helpviewer_keywords:
- LNK1332
ms.assetid: b31d5ca0-c27f-4177-896b-2637dccbde24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b256c61b9e9de6bf19e754054de1f55fcdec5f0b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094518"
---
# <a name="linker-tools-error-lnk1332"></a>Erreur des outils Éditeur de liens LNK1332

détecté\<nombre > Windows Runtime importés dans un module et les types définis dans un autre module

Quand il produit la cible actuelle, l’éditeur de liens détecté <`count`> types Windows Runtime, chacun d’eux est importé dans un module et également défini dans un autre module.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Corrigez toutes les erreurs des LNK2039 dans la build en fonction de la suggestion dans le message d’erreur.

## <a name="see-also"></a>Voir aussi

[Erreur des outils Éditeur de liens LNK2039](../../error-messages/tool-errors/linker-tools-error-lnk2039.md)<br/>
[Erreurs et avertissements des outils Éditeur de liens](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)