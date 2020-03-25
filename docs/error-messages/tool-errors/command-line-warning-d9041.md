---
title: Avertissement de ligne de commande D9041
ms.date: 11/04/2016
f1_keywords:
- D9041
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
ms.openlocfilehash: 7c685a1ca3195ad4ab52bab8b5d32b1a51534b24
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196573"
---
# <a name="command-line-warning-d9041"></a>Avertissement de ligne de commande D9041

valeur’value’non valide pour'/option'; en supposant « valeur »; Ajouter'/Analyze’aux options de ligne de commande lors de la spécification de cet avertissement

Un numéro d’avertissement d’analyse du code a été ajouté à l’option de ligne de commande **/WD**, **/We**, **/WO**ou **/WL** sans spécifier également l’option de ligne de commande **/analyze** . Pour remédier à cette erreur, ajoutez l’option de ligne de commande **/analyze** ou supprimez le numéro d’avertissement non valide de l’option de ligne de commande **/w** appropriée.

## <a name="example"></a>Exemple

L’exemple de ligne de commande suivant génère l’avertissement D9041 :

```
cl /EHsc /LD /wd6001 filename.cpp
```

Pour résoudre l’avertissement, ajoutez l’option de ligne de commande **/analyze** . Si **/analyze** n’est pas pris en charge sur votre version du compilateur, supprimez le numéro d’avertissement non valide de l’option **/WD** .

## <a name="see-also"></a>Voir aussi

[Erreurs de ligne de commande D8000 à D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[Options du compilateur MSVC](../../build/reference/compiler-options.md)
