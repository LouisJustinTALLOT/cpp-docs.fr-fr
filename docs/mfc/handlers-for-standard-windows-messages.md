---
title: Gestionnaires pour les messages Windows standard
ms.date: 11/04/2016
f1_keywords:
- afx_msg
helpviewer_keywords:
- Windows messages [MFC], handlers
- message handling [MFC], Windows message handlers
- handler functions, standard Windows messages
- functions [MFC], handler
- messages [MFC], Windows
ms.assetid: 19412a8b-2c38-4502-81da-13c823c7e36c
ms.openlocfilehash: 9a136caf3a1d22151cb9cfd48e1cd3f999ab51ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370503"
---
# <a name="handlers-for-standard-windows-messages"></a>Gestionnaires pour les messages Windows standard

Les gestionnaires par défaut**WM_** pour les messages Windows standard ( `CWnd`WM_ ) sont prédéfinis en classe . La bibliothèque de classes base les noms de ces gestionnaires sur le nom du message. Par exemple, le gestionnaire du **message WM_PAINT** `CWnd` est déclaré en tant que :

`afx_msg void OnPaint();`

Le mot clé **afx_msg** suggère l’effet du mot clé **virtuel** CMD `CWnd` en distinguant les gestionnaires des autres fonctions des membres. Notez, toutefois, que ces fonctions ne sont pas réellement virtuelles ; elles sont plutôt implémentées dans les tables des messages. Les tables des messages dépendent uniquement des macros de préprocesseur standard, et non des extensions au langage C++. Le mot clé **afx_msg** se résout à l’espace blanc après le prétraitement.

Pour remplacer un gestionnaire défini dans une classe de base, il vous suffit de définir une fonction avec le même prototype dans votre classe dérivée et de créer une entrée dans la table des messages du gestionnaire. Le gestionnaire "substitue" tout gestionnaire du même nom dans n'importe laquelle des classes de base de vos classes.

Dans certains cas, le gestionnaire doit appeler le gestionnaire de remplacement dans la classe de base pour que la classe de base et Windows puissent traiter le message. L'emplacement où vous appelez le gestionnaire de classe de base dans votre substitution dépend des circonstances. Parfois vous devez appeler le gestionnaire de classe de base en premier et parfois en dernier. Parfois vous appelez le gestionnaire de classe de base de manière conditionnelle, si vous choisissez de ne pas traiter le message vous-même. Parfois vous devez appeler le gestionnaire de classe de base, puis exécuter de manière conditionnelle votre propre code gestionnaire, selon la valeur et l'état retourné par le gestionnaire de la classe de base.

> [!CAUTION]
> Il n’est pas sécurisé de modifier les arguments passés dans un gestionnaire si vous envisagez de les transmettre à un gestionnaire de la classe de base. Par exemple, vous pourriez être tenté de modifier `OnChar` *l’argument nChar* du gestionnaire (pour convertir en uppercase, par exemple). Ce comportement est assez obscur, mais si vous `CWnd` avez `SendMessage` besoin d’accomplir cet effet, utilisez la fonction du membre à la place.

Comment déterminez-vous la bonne façon de passer outre à un message donné Lorsque le `OnCreate` Maître de [classe](reference/mfc-class-wizard.md) écrit le squelette de la fonction de gestionnaire pour un message donné - un gestionnaire pour **WM_CREATE**, par exemple - il esquisse sous la forme de la fonction de membre remplacé recommandée. L’exemple suivant recommande que le gestionnaire appelle d’abord le gestionnaire de la classe de base et ne procède qu’à la condition qu’il ne retourne pas -1.

[!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]

Par convention, les noms de ces gestionnaires commencent par le préfixe "On". Certains de ces gestionnaires n’occupent aucun argument, tandis que d’autres en ont plusieurs. Certains ont également un type de retour autre que **vide**. Les gestionnaires par défaut pour **tous** les WM_ messages sont documentés `CWnd` dans la *référence MFC* comme fonctions membres de la classe dont les noms commencent par "On". Les déclarations de `CWnd` fonction de membre sont préfixées avec **afx_msg**.

## <a name="see-also"></a>Voir aussi

[Déclaration des fonctions de gestionnaire de messages](../mfc/declaring-message-handler-functions.md)
