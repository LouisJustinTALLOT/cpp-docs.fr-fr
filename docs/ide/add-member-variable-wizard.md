---
title: Assistant Ajout de variable membre
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.variable.overview
helpviewer_keywords:
- Add Member Variable Wizard [C++]
ms.assetid: 73e8fa99-ac1a-42e2-8fc2-4684b9eb6d4d
ms.openlocfilehash: ea9b52c7448ee46a15c5da541784378d2b625d88
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598586"
---
# <a name="add-member-variable-wizard"></a>Assistant Ajout de variable membre

Cet Assistant ajoute une déclaration de variable membre au fichier d’en-tête et, selon les options, il peut ajouter du code au fichier .cpp. Une fois que vous avez ajouté la variable membre avec l’Assistant, vous pouvez modifier le code dans l’environnement de développement.

- **Accès**

   Définit l’accès à la variable membre. Les modificateurs d’accès sont des mots clés spécifiant l’accès des autres classes à la variable membre. Pour plus d’informations sur la spécification de l’accès, consultez [Contrôle d’accès aux membres](../cpp/member-access-control-cpp.md). Le niveau d’accès à la variable membre est défini par défaut sur **public**.

- [public](../cpp/public-cpp.md)

- [protected](../cpp/protected-cpp.md)

- [private](../cpp/private-cpp.md)

- **Type de variable**

   Définit le type de retour pour la variable de membre que vous ajoutez.

   - Si vous ajoutez une variable membre qui n’est pas un contrôle de boîte de dialogue, sélectionnez dans la liste des types disponibles.

      Pour plus d’informations sur les types, consultez [Types fondamentaux](../cpp/fundamental-types-cpp.md).

      |||
      |-|-|
      |**char**|**short**|
      |**double**|**unsigned char**|
      |**float**|**unsigned int**|
      |**int**|**unsigned long**|
      |**long**||

   - Si vous ajoutez une variable membre pour un contrôle de boîte de dialogue, cette zone est renseignée avec le type de l’objet retourné pour un contrôle ou une valeur. Si vous sélectionnez **Contrôle**, **Type de variable** spécifie la classe de base du contrôle que vous sélectionnez dans la zone **ID de contrôle**. Si le contrôle de boîte de dialogue peut contenir une valeur et si vous sélectionnez **Valeur**, **Type de variable** spécifie le type approprié pour la valeur que le contrôle peut contenir. Pour plus d’informations, consultez [Contrôles de boîtes de dialogue et types de variables](../ide/dialog-box-controls-and-variable-types.md).

      Cette valeur dépend de la sélection dans **ID de contrôle** et ne peut pas être modifiée.

- **Nom de la variable**

   Définit le nom de la variable membre que vous ajoutez. Les variables membres commencent généralement par la chaîne d’identification « m_ », qui vous est fournie par défaut.

- **Variable de contrôle**

   Indique que la variable membre gère un contrôle dans une boîte de dialogue avec prise en charge de [l’échange de données et de la validation des données](../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations, consultez [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange). Cette option est disponible seulement pour les variables membres ajoutées à des classes dérivées de [CDialog](../mfc/reference/cdialog-class.md). Cochez cette case pour activer les options **ID de contrôle** et **Type de contrôle**.

- **ID de contrôle**

   Définit l’ID pour la variable de contrôle que vous ajoutez. Dans la liste, sélectionnez l’ID pour le type de contrôle pour lequel vous ajoutez la variable membre. La liste est active seulement quand la case **Variable de contrôle** est cochée, et elle est limité aux ID des contrôles déjà ajoutés à la boîte de dialogue. Par exemple, pour le bouton **OK** standard, l’ID de contrôle est **IDOK**.

   |Option|Description|
   |------------|-----------------|
   |**Contrôle**|Cette option est définie par défaut pour le type de contrôle. Elle gère le contrôle lui-même et non pas l’état ou le contenu du contrôle (comme vous pourriez vouloir le faire avec une zone de liste, une zone de liste modifiable ou une zone d’édition).|
   |**Valeur**|Cette option est disponible seulement pour les types de contrôles qui peuvent contenir une valeur (comme une zone d’édition) ou refléter un état (comme une case à cocher), et pour lesquels vous pouvez gérer la plage de valeurs, le contenu ou l’état. Pour plus d’informations, consultez [Contrôles de boîtes de dialogue et types de variables](../ide/dialog-box-controls-and-variable-types.md).|

- **Catégorie**

   Spécifie si la variable est basée sur un type de contrôle ou sur la valeur du contrôle.

- **Type de contrôle**

   Définit le type de contrôle ajouté. Vous ne pouvez pas changer cette case. Par exemple, un bouton a le type de contrôle **BUTTON** et une zone de liste modifiable a le type de contrôle **COMBOBOX**. Pour plus d’informations, consultez [Contrôles de boîtes de dialogue et types de variables](../ide/dialog-box-controls-and-variable-types.md).

- **Nombre maximal de caractères**

   Disponible seulement quand **Type de Variable** est défini sur [CString](../atl-mfc-shared/reference/cstringt-class.md). Indique le nombre maximal de caractères que le contrôle peut contenir.

- **Valeur minimale**

   Disponible seulement quand le type de variable est **BOOL**, `int`, **UINT**, **long**, `DWORD`, **float**, **double**, **BYTE**, **short**, [COLECurrency](../mfc/reference/colecurrency-class.md) ou [CTime](../atl-mfc-shared/reference/ctime-class.md). Indique la plus petite valeur acceptable pour une plage de mise à l’échelle ou de dates.

- **Valeur maximale**

   Disponible seulement quand le type de variable est **BOOL**, `int`, **UINT**, **long**, `DWORD`, **float**, **double**, **BYTE**, **short**, `COLECurrency` ou `CTime`. Indique la plus haute valeur acceptable pour une plage de mise à l’échelle ou de dates.

- **Fichier .h**

   Pour les contrôles ActiveX, dont les variables membres nécessitent une classe wrapper. Définit le nom du fichier d’en-tête pour ajouter la déclaration de classe.

- **Fichier .cpp**

   Pour les contrôles ActiveX, dont les variables membres nécessitent une classe wrapper. Définit le nom du fichier d’implémentation pour ajouter la définition de classe.

- **Commentaire**

   Fournit un commentaire dans le fichier d’en-tête pour la variable membre.

## <a name="see-also"></a>Voir aussi

[Ajout d’une variable membre](../ide/adding-a-member-variable-visual-cpp.md)