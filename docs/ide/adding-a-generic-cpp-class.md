---
title: Ajouter une classe C++ générique
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.adding.generic
- vc.codewiz.class.generic
helpviewer_keywords:
- Visual C++, classes
- generic classes, adding
- generic classes
- generic C++ class wizard [C++]
ms.assetid: e95a5a14-dbed-4edc-8551-344fe48613cb
ms.openlocfilehash: e81ea442578e69bdd28301eba8f70561f6aa76c6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230543"
---
# <a name="add-a-generic-c-class"></a>Ajouter une classe C++ générique

Vous pouvez ajouter une classe C++ générique via **l’affichage de classes**. Une classe C++ générique est une classe que vous définissez ou qui est dérivée d’une classe que vous définissez.

**Pour ajouter une classe C++ générique à un projet**

1. Dans **Affichage de classes**, cliquez avec le bouton droit sur le projet auquel vous voulez ajouter la nouvelle classe, choisissez **Ajouter**, puis **Classe**.

1. Dans la boîte de dialogue [Ajouter une classe](../ide/add-class-dialog-box.md), dans le volet Modèles, sélectionnez **Classe C++**. Sélectionnez **Ajouter** pour afficher l’[Assistant Classe C++ générique](#generic-c-class-wizard).

1. Dans l’Assistant, indiquez le nom de la classe, puis définissez les paramètres ou acceptez les valeurs par défaut.

1. Pour fermer l’Assistant et afficher la nouvelle classe C++ générique du projet, sélectionnez **Terminer**.

## <a name="in-this-section"></a>Contenu de cette section

- [Assistant classe C++ générique](#generic-c-class-wizard)

## <a name="generic-c-class-wizard"></a>Assistant Classe C++ générique

Ajoute une classe C++ générique à un projet. La classe n’hérite pas d’ATL ni de MFC.

- **Nom de la classe**

  Définit le nom de la nouvelle classe.

- **Fichier .h**

  Définit le nom du fichier d’en-tête de la nouvelle classe. Par défaut, ce nom est basé sur celui que vous fournissez dans **Nom de classe**. Pour enregistrer le fichier d’en-tête à l’emplacement de votre choix, ou pour ajouter la déclaration de classe à un fichier existant, cliquez sur le bouton de sélection (**...**). Si vous spécifiez un fichier existant et que vous sélectionnez **Terminer**, l’Assistant vous invite à spécifier si la déclaration de classe doit être ajoutée au contenu du fichier. Pour ajouter la déclaration, sélectionnez **Oui** ; pour revenir à l’Assistant et spécifier un autre nom de fichier, sélectionnez **Non**.

- **Fichier .cpp**

  Définit le nom du fichier d’implémentation de la nouvelle classe. Par défaut, ce nom est basé sur celui que vous fournissez dans **Nom de classe**. Pour enregistrer le fichier d’implémentation à l’emplacement de votre choix, ou pour ajouter la définition de classe à un fichier existant, cliquez sur le bouton de sélection (**...**). Si vous spécifiez un fichier existant et que vous sélectionnez **Terminer**, l’Assistant vous invite à spécifier si la définition de classe doit être ajoutée au contenu du fichier. Pour ajouter la définition, sélectionnez **Oui** ; pour revenir à l’Assistant et spécifier un autre nom de fichier, sélectionnez **Non**.

- **Classe de base**

  Définit la classe de base de la nouvelle classe.

- **y accéder**

  Définit l’accès aux membres de la classe de base de la nouvelle classe. Les modificateurs d’accès sont des mots clés spécifiant le niveau d’accès des autres classes aux fonctions membres de la classe. Pour plus d’informations sur la façon de spécifier l’accès, consultez [Contrôle d’accès aux membres](../cpp/member-access-control-cpp.md). Par défaut, le niveau d’accès de la classe a la valeur **`public`** .

  - **`public`**
  - **`protected`**
  - **`private`**
  - **Par défaut** (aucun modificateur d’accès n’est généré.)

- **Destructeur virtuel**

  Indique si le destructeur de classe est virtuel. L’utilisation d’un destructeur virtuel permet de garantir que le destructeur correct est appelé en cas de suppression d’instances de classes dérivées.

- **En ligne**

  Génère à la fois le constructeur de classe et la définition de classe comme fonctions inline dans le fichier d’en-tête.

- **Managé**

  Quand la case est cochée, une classe managée et un fichier d’en-tête sont ajoutés. Quand la case est décochée, une classe native et un fichier d’en-tête sont ajoutés.
