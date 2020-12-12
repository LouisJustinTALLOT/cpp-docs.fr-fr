---
description: 'En savoir plus sur : Command-Line AVERTISSEMENT D9041'
title: Avertissement de ligne de commande D9041
ms.date: 11/04/2016
f1_keywords:
- D9041
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
ms.openlocfilehash: d6226d4e5dd89176c0ed3722a9fd24e1244cacac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119760"
---
# <a name="command-line-warning-d9041"></a>Avertissement de ligne de commande D9041

> valeur'*option-value*'non valide pour'/*option-Name*'; en supposant «*valeur supposée*»; Ajouter'/Analyze’aux options de ligne de commande lors de la spécification de cet avertissement

Un numéro d’avertissement d’analyse du code a été ajouté à l’option de ligne de commande,, **`/wd`** **`/we`** **`/wo`** ou **`/wl`** sans spécifier également l' **`/analyze`** option de ligne de commande. Pour remédier à cette erreur, ajoutez l' **`/analyze`** option de ligne de commande ou supprimez le numéro d’avertissement non valide de l' **`/w`** option de ligne de commande appropriée.

## <a name="example"></a>Exemple

L’exemple de ligne de commande suivant génère l’avertissement D9041 :

```cmd
cl /EHsc /LD /wd6001 filename.cpp
```

Pour résoudre l’avertissement, ajoutez l' **`/analyze`** option de ligne de commande. Si **`/analyze`** n’est pas pris en charge dans votre version du compilateur, supprimez le numéro d’avertissement non valide de l' **`/wd`** option.

## <a name="see-also"></a>Voir aussi

[Erreurs de ligne de commande D8000 à D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[Options du compilateur MSVC](../../build/reference/compiler-options.md)
