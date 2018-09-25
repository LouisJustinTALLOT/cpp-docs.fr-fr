---
title: Assistant Classe C++ générique | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.class.generic
dev_langs:
- C++
helpviewer_keywords:
- Generic C++ Class Wizard [C++]
ms.assetid: aa95be9e-fc1b-45db-a11d-0d32c4929077
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b104c0631fde3164ef4299cead47caba912874b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431084"
---
# <a name="generic-c-class-wizard"></a>Assistant Classe C++ générique

Ajoute une classe C++ générique à un projet. La classe n’hérite pas d’ATL ni de MFC.

- **Nom de classe**

   Définit le nom de la nouvelle classe.

- **Fichier .h**

   Définit le nom du fichier d’en-tête de la nouvelle classe. Par défaut, ce nom est basé sur celui que vous fournissez dans **Nom de classe**. Pour enregistrer le fichier d’en-tête à l’emplacement de votre choix ou pour ajouter la déclaration de classe à un fichier existant, cliquez sur le bouton de sélection (**...**). Si vous spécifiez un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si la déclaration de classe doit être ajoutée au contenu du fichier. Pour ajouter la déclaration, cliquez sur **Oui** ; pour revenir à l’Assistant et spécifier un autre nom de fichier, cliquez sur **Non**.

- **Fichier .cpp**

   Définit le nom du fichier d’implémentation de la nouvelle classe. Par défaut, ce nom est basé sur celui que vous fournissez dans **Nom de classe**. Pour enregistrer le fichier d’implémentation à l’emplacement de votre choix ou pour ajouter la définition de classe à un fichier existant, cliquez sur le bouton de sélection (**...**). Si vous spécifiez un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si la définition de classe doit être ajoutée au contenu du fichier. Pour ajouter la définition, cliquez sur **Oui** ; pour revenir à l’Assistant et spécifier un autre nom de fichier, cliquez sur **Non**.

- **Classe de base**

   Définit la classe de base de la nouvelle classe.

- **Accès**

   Définit l’accès aux membres de la classe de base de la nouvelle classe. Les modificateurs d’accès sont des mots clés spécifiant le niveau d’accès des autres classes aux fonctions membres de la classe. Pour plus d’informations sur la spécification de l’accès, consultez [Contrôle d’accès aux membres](../cpp/member-access-control-cpp.md). Par défaut, le niveau d’accès de la classe a la valeur `public`.

   - `public`

   - `protected`

   - `private`

   - **Par défaut** (aucun modificateur d’accès n’est généré.)

- **Destructeur virtuel**

   Indique si le destructeur de classe est virtuel. L’utilisation d’un destructeur virtuel permet de garantir que le destructeur correct est appelé en cas de suppression d’instances de classes dérivées.

- **Inline**

   Génère à la fois le constructeur de classe et la définition de classe comme fonctions inline dans le fichier d’en-tête.

- **Managée**

   Quand la case est cochée, une classe managée et un fichier d’en-tête sont ajoutés. Quand la case est décochée, une classe native et un fichier d’en-tête sont ajoutés.

## <a name="see-also"></a>Voir aussi

[Ajout d’une classe C++ générique](../ide/adding-a-generic-cpp-class.md)