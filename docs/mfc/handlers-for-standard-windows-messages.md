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
ms.openlocfilehash: d967341cdb0197f1157ab9d253072f3d0d7aa46f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223146"
---
# <a name="handlers-for-standard-windows-messages"></a>Gestionnaires pour les messages Windows standard

Les gestionnaires par défaut pour les messages Windows standard (**WM_**) sont prédéfinis dans la classe `CWnd` . La bibliothèque de classes base les noms de ces gestionnaires sur le nom du message. Par exemple, le gestionnaire du message **WM_PAINT** est déclaré dans `CWnd` en tant que :

`afx_msg void OnPaint();`

Le mot clé **afx_msg** suggère l’effet du **`virtual`** mot clé C++ en distinguant les gestionnaires des autres `CWnd` fonctions membres. Notez, toutefois, que ces fonctions ne sont pas réellement virtuelles ; elles sont plutôt implémentées dans les tables des messages. Les tables des messages dépendent uniquement des macros de préprocesseur standard, et non des extensions au langage C++. Le mot clé **afx_msg** correspond à un espace blanc après le prétraitement.

Pour remplacer un gestionnaire défini dans une classe de base, il vous suffit de définir une fonction avec le même prototype dans votre classe dérivée et de créer une entrée dans la table des messages du gestionnaire. Le gestionnaire "substitue" tout gestionnaire du même nom dans n'importe laquelle des classes de base de vos classes.

Dans certains cas, le gestionnaire doit appeler le gestionnaire de remplacement dans la classe de base pour que la classe de base et Windows puissent traiter le message. L'emplacement où vous appelez le gestionnaire de classe de base dans votre substitution dépend des circonstances. Parfois vous devez appeler le gestionnaire de classe de base en premier et parfois en dernier. Parfois vous appelez le gestionnaire de classe de base de manière conditionnelle, si vous choisissez de ne pas traiter le message vous-même. Parfois vous devez appeler le gestionnaire de classe de base, puis exécuter de manière conditionnelle votre propre code gestionnaire, selon la valeur et l'état retourné par le gestionnaire de la classe de base.

> [!CAUTION]
> Il n’est pas sécurisé de modifier les arguments passés dans un gestionnaire si vous envisagez de les transmettre à un gestionnaire de la classe de base. Par exemple, vous pouvez être tenté de modifier l’argument *nchar* du `OnChar` Gestionnaire (pour convertir en majuscules, par exemple). Ce comportement est relativement obscur, mais si vous devez effectuer cet effet, utilisez la `CWnd` fonction membre à la `SendMessage` place.

Comment déterminez-vous la méthode appropriée pour remplacer un message donné lorsque l' [Assistant classe](reference/mfc-class-wizard.md) écrit la structure de la fonction gestionnaire pour un message donné (un `OnCreate` Gestionnaire pour **WM_CREATE**, par exemple), il est esquissé sous la forme de la fonction membre substituée recommandée. L’exemple suivant recommande que le gestionnaire appelle d’abord le gestionnaire de classe de base et se poursuive uniquement à condition qu’il ne retourne pas-1.

[!code-cpp[NVC_MFCMessageHandling#3](codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]

Par convention, les noms de ces gestionnaires commencent par le préfixe "On". Certains de ces gestionnaires n’occupent aucun argument, tandis que d’autres en ont plusieurs. Certains ont également un type de retour autre que **`void`** . Les gestionnaires par défaut de tous les messages **WM_** sont documentés dans la *référence MFC* en tant que fonctions membres de la classe `CWnd` dont les noms commencent par « on ». Les déclarations de fonctions membres dans `CWnd` sont précédées de **afx_msg**.

## <a name="see-also"></a>Voir aussi

[Déclaration des fonctions de gestionnaire de messages](declaring-message-handler-functions.md)
