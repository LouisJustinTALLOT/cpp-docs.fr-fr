---
title: Ajouter une fonction membre
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.member.function
- vc.codewiz.function.overview
helpviewer_keywords:
- member functions, adding to classes
- classes [C++], adding members
- add member function wizard [C++]
ms.assetid: 55b25ddb-541d-44ed-957c-974ef91cfc85
ms.openlocfilehash: 0e63771e3e01c3829e20d2fe62fa2caf0f8b26f5
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040780"
---
# <a name="add-a-member-function"></a>Ajouter une fonction membre

Dans **l’affichage de classes**, vous pouvez ajouter une fonction membre à n’importe quelle classe. Dans ce cas, une déclaration est ajoutée au fichier d’en-tête et un corps de fonction membre stub est ajouté au fichier d’implémentation de la classe, que vous pouvez ensuite modifier.

**Pour ajouter une fonction membre à une classe**

1. Dans **l’affichage de classes**, développez le nœud du projet afin d’afficher ses classes. (Pour ouvrir **l’affichage de classes**, dans la barre de menus, choisissez **Afficher**, **Affichage de classes**.)

1. Ouvrez le menu contextuel de la classe à laquelle vous souhaitez ajouter une fonction membre, puis choisissez **Ajouter**, **Ajouter une fonction**.

1. Fournissez les détails appropriés sur la fonction membre. Pour plus d’informations, consultez [Assistant Ajout de fonction membre](#add-member-function-wizard).

1. Cliquez sur le bouton **Terminer** pour générer le code de la fonction membre.

## <a name="in-this-section"></a>Contenu de cette section

- [Assistant Ajout d’une fonction membre](#add-member-function-wizard)

## <a name="add-member-function-wizard"></a>Assistant Ajout de fonction membre

Cet Assistant ajoute une déclaration de fonction membre au fichier d’en-tête. Il ajoute également une implémentation de fonction membre stub au fichier d’implémentation pour la classe sélectionnée.

Une fois que vous avez ajouté la fonction membre avec l’Assistant, vous pouvez modifier le code dans l’environnement de développement.

- **Type de retour**

  Définit le type de retour pour la fonction membre que vous ajoutez. Vous pouvez fournir votre propre type de retour ou le sélectionner dans la liste des types disponibles. Pour plus d’informations sur les types, consultez [Types fondamentaux](../cpp/fundamental-types-cpp.md).

:::row:::
   :::column span="":::
      **`char`**\
      **`double`**\
      **`float`**\
      **`int`**
   :::column-end:::
   :::column span="":::
      **`long`**\
      **`short`**\
      **`unsigned char`**\
      **`unsigned int`**
   :::column-end:::
   :::column span="":::
      **`unsigned long`**\
      **`void`**\
      `HRESULT`
   :::column-end:::
:::row-end:::

- **Nom de la fonction**

  Définit le nom de la fonction membre que vous ajoutez.

- **Type de paramètre**

  Définit le type de paramètre que vous ajoutez pour la fonction membre, si elle possède des paramètres. Vous pouvez fournir votre propre type de paramètre ou le sélectionner dans la liste des types disponibles.

:::row:::
   :::column span="":::
      **`char`**\
      **`double`**\
      **`float`**
   :::column-end:::
   :::column span="":::
      **`int`**\
      **`long`**\
      **`short`**
   :::column-end:::
   :::column span="":::
      **`unsigned char`**\
      **`unsigned int`**\
      **`unsigned long`**
   :::column-end:::
:::row-end:::

- **Nom du paramètre**

  Définit le nom d’un paramètre que vous ajoutez pour la fonction membre, si elle possède des paramètres.

- **Liste de paramètres**

  Affiche la liste des paramètres que vous avez ajoutés à la fonction membre. Pour ajouter un paramètre à la liste, spécifiez un type et un nom dans les zones **Type de paramètre** et **Nom du paramètre**, puis sélectionnez **Ajouter**. Pour supprimer un paramètre de la liste, sélectionnez-le et sélectionnez **Supprimer**.

- **y accéder**

  Définit l’accès à la fonction membre. Les modificateurs d’accès sont des mots clés spécifiant l’accès des autres classes à la fonction membre. Pour plus d’informations sur la spécification de l’accès, consultez [Contrôle d’accès aux membres](../cpp/member-access-control-cpp.md). Par défaut, le niveau d’accès à la fonction membre est défini sur **`public`** .

  - [public](../cpp/public-cpp.md)
  - [protected](../cpp/protected-cpp.md)
  - [private](../cpp/private-cpp.md)

  Vérifiez si la nouvelle fonction membre est statique ou virtuelle, et si elle est inline ou pure. Si vous définissez la fonction membre comme pure, la case **Virtual** est cochée et la case **Inline** n’est plus disponible. Par défaut, la fonction membre est non statique et non virtuelle.

  | Option | Description |
  |--------|-------------|
  | [Statique](../cpp/storage-classes-cpp.md) |  Spécifie que la fonction agit comme une fonction globale et peut être appelée à l’extérieur de la classe, même sans instanciation de classe. La fonction membre n’a pas accès aux membres non statiques. Une fonction membre spécifiée comme `Static` ne peut pas être virtuelle. |
  | [Virtuelle](../cpp/virtual-cpp.md) | Garantit que la fonction membre correcte est appelée pour un objet, quelle que soit l’expression utilisée pour créer l’appel de fonction membre. Une fonction membre spécifiée comme `Virtual` ne peut pas être statique. |
  | **FCP** | Indique qu’aucune implémentation n’est fournie pour la fonction membre virtuelle déclarée. **Pure** peut être spécifié uniquement sur les fonctions membres virtuelles. Une classe contenant au moins une fonction membre virtuelle pure est considérée comme une classe abstraite. Les classes dérivées de la classe abstraite doivent implémenter la fonction membre virtuelle pure, sinon elles aussi sont des classes abstraites. |
  | [En ligne](../cpp/inline-functions-cpp.md) | Indique au compilateur d’insérer une copie du corps de la fonction membre à chaque emplacement où la fonction membre est appelée. Une fonction membre spécifiée comme **Inline** ne peut pas être pure. |

- **Fichier .cpp**

  Définit l’emplacement du fichier où l’implémentation de fonction membre stub est écrite. Par défaut, il s’agit du fichier .cpp de la classe à laquelle la fonction membre est ajoutée. Sélectionnez le bouton de sélection pour changer le nom du fichier. L’implémentation de la fonction membre est ajoutée au contenu du fichier sélectionné.

- **Commentaire**

  Fournit un commentaire dans le fichier d’en-tête pour la fonction membre.

- **Signature de fonction**

  Affiche la fonction membre textuelle à partir du code quand vous sélectionnez **Terminer**. Vous ne pouvez pas modifier le texte dans cette zone. Pour modifier la fonction membre, changez les zones appropriées de l’Assistant.
