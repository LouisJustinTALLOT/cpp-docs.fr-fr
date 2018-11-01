---
title: Avertissement de ligne de commande D9041
ms.date: 11/04/2016
f1_keywords:
- D9041
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
ms.openlocfilehash: 79bdafcd4ed6af061b9c0ee27aae6eed6bc981a0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513917"
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
[Options du compilateur](../../build/reference/compiler-options.md)