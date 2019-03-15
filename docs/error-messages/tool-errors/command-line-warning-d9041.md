---
title: Avertissement de ligne de commande D9041
ms.date: 11/04/2016
f1_keywords:
- D9041
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
ms.openlocfilehash: 2311c61c4d661d58302308f06b08971f94cdacab
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816306"
---
# <a name="command-line-warning-d9041"></a>Avertissement de ligne de commande D9041

valeur non valide 'value' pour '/ option' ; en supposant que 'value' ; Ajoutez ' /analyze ' aux options de ligne de commande lors de la spécification de cet avertissement

Un numéro d’avertissement de l’analyse du Code a été ajouté à la **WD**, **/we**, **wo**, ou **/wl** option de ligne de commande sans spécifier également le **/ analyze** option de ligne de commande. Pour remédier à cette erreur, ajoutez le **/ analyze** option de ligne de commande, ou supprimez le numéro d’avertissement non valide approprié **/w** option de ligne de commande.

## <a name="example"></a>Exemple

L’exemple de ligne de commande suivant génère l’avertissement D9041 :

```
cl /EHsc /LD /wd6001 filename.cpp
```

Pour résoudre l’avertissement, ajoutez le **/ analyze** option de ligne de commande. Si **/ analyze** est ne pas pris en charge sur votre version du compilateur, supprimez le numéro d’avertissement non valide à partir de la **WD** option.

## <a name="see-also"></a>Voir aussi

[Erreurs de ligne de commande D8000 à D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[Options du compilateur MSVC](../../build/reference/compiler-options.md)