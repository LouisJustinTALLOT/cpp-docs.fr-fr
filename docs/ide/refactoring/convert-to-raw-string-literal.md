---
title: Convertir en littéral de chaîne brut
ms.date: 11/16/2016
ms.assetid: fffbfee4-66ee-42ba-aeb9-df07fb702c51
ms.openlocfilehash: bf492e6796b9d2342b5952abb093bddd5ede114b
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51692591"
---
# <a name="convert-to-raw-string-literal"></a>Convertir en littéral de chaîne brut

**Quoi :** vous permet de transformer une chaîne en littéral de chaîne brute C++.

**Quand :** vous avez une chaîne avec des caractères d’échappement qui ne doivent pas être traités comme des caractères d’échappement.

**Pourquoi :** vous pouvez doubler la séquence d’échappement, mais cela aboutit souvent à des chaînes illisibles et qui prêtent à confusion.  L’utilisation de littéraux de chaînes brutes facilite la lecture des chaînes.

**Comment :**

1. placez le curseur texte ou de la souris sur la chaîne faisant l’objet d’une séquence d’échappement à convertir.

   ![Code mis en surbrillance](images/stringliteral_highlight.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Convertir en littéral de chaîne brute** dans le menu contextuel.
   * **Souris**
     * Cliquez avec le bouton droit sur le code et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Convertir en littéral de chaîne brute** dans le menu contextuel.
     * Cliquez sur l’icône ![Ampoule](images/bulb.png) qui apparaît dans la marge de gauche et sélectionnez **Convertir en littéral de chaîne brute** dans le menu contextuel.

1. La chaîne est immédiatement convertie en littéral de chaîne brute.

   ![Littéral de chaîne brute, résultat](images/stringliteral_result.png)