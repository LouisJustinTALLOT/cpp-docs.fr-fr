---
description: 'En savoir plus sur : prise en charge MAPI dans les MFC'
title: Prise en charge MAPI dans MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, MAPI support
- MAPI support in MFC
- CDocument class [MFC], and MAPI
- OnUpdateFileSendMail method [MFC]
- MAPI, MFC
- OnFileSendMail method [MFC]
ms.assetid: cafbecb1-0427-4077-b4b8-159bae5b49b8
ms.openlocfilehash: 289ad61894efd5c08d3a50d8c50e3ac6ee518a25
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280753"
---
# <a name="mapi-support-in-mfc"></a>Prise en charge MAPI dans MFC

MFC fournit la prise en charge d’un sous-ensemble de l’interface MAPI (Microsoft Messaging Application Program Interface) dans la classe `CDocument` . En particulier, `CDocument` contient des fonctions membres qui déterminent si la prise en charge de la messagerie est présente sur l’ordinateur de l’utilisateur final et, si c’est le cas, active une commande Envoyer un message dont l’ID de commande standard est ID_FILE_SEND_MAIL. La fonction de gestionnaire MFC pour cette commande permet à l'utilisateur d'envoyer un document via la messagerie électronique.

> [!TIP]
> Bien que MFC n'encapsule pas l'ensemble des fonctions MAPI, vous pouvez toujours appeler les fonctions MAPI directement, de la même manière que vous pouvez appeler les fonctions API Win32 directement à partir des programmes MFC.

L'activation de la commande Envoyer un message dans votre application est très simple. MFC fournit l’implémentation pour empaqueter un document (autrement dit, un `CDocument` objet dérivé de) en tant que pièce jointe et l’envoyer en tant que message électronique. Cette pièce jointe est équivalente à une commande d'enregistrement de fichier qui stocke (sérialise) le contenu du document dans le message électronique. Cette implémentation appelle le client de messagerie sur l’ordinateur de l’utilisateur pour permettre à ce dernier d’adresser le message et d’y ajouter un objet et un texte. Les utilisateurs voient l'interface usuelle de leur application de messagerie usuelle. Cette fonctionnalité est fournie par deux `CDocument` fonctions membres : `OnFileSendMail` et `OnUpdateFileSendMail` .

L'interface MAPI doit lire le fichier pour envoyer la pièce jointe. Si l'application garde son fichier de données ouvert pendant un appel de fonction `OnFileSendMail`, le fichier doit être ouvert avec un mode de partage qui autorise plusieurs processus à y accéder.

> [!NOTE]
> Une version de substitution de `OnFileSendMail` pour la classe `COleDocument` traite correctement les documents composés.

#### <a name="to-implement-a-send-mail-command-with-mfc"></a>Pour implémenter une commande Envoyer un message avec MFC

1. Utilisez l'éditeur de menu de Visual C++ pour ajouter un élément de menu dont l'ID de commande est ID_FILE_SEND_MAIL.

   Cet ID de commande est fourni par le framework dans AFXRES.H. La commande peut être ajoutée à n’importe quel menu, mais elle est généralement ajoutée au menu **fichier** .

1. Ajoutez manuellement le code suivant à la table des messages de votre document :

   [!code-cpp[NVC_MFCDocView#9](codesnippet/cpp/mapi-support-in-mfc_1.cpp)]

    > [!NOTE]
    >  Cette table des messages fonctionne pour un document dérivé de `CDocument` ou `COleDocument` : elle récupère la classe de base appropriée dans les deux cas, même si la table des messages est dans votre classe de document dérivée.

1. Générez votre application.

Si la prise en charge de la messagerie est disponible, MFC active votre élément de menu avec `OnUpdateFileSendMail` et traite ensuite la commande avec `OnFileSendMail`. Si elle n'est pas disponible, MFC supprime automatiquement votre élément de menu afin que l'utilisateur ne le voit pas.

> [!TIP]
> Au lieu d’ajouter manuellement les entrées de la table des messages comme décrit précédemment, vous pouvez utiliser l' [Assistant classe](reference/mfc-class-wizard.md) de classe pour mapper des messages à des fonctions. Pour plus d’informations, consultez [mappage de messages à des fonctions](reference/mapping-messages-to-functions.md).

Pour obtenir des informations connexes, consultez la vue d’ensemble de [MAPI](mapi.md) .

Pour plus d’informations sur les `CDocument` fonctions membres qui activent MAPI, consultez :

- [CDocument::OnFileSendMail](reference/cdocument-class.md#onfilesendmail)

- [CDocument::OnUpdateFileSendMail](reference/cdocument-class.md#onupdatefilesendmail)

- [COleDocument::OnFileSendMail](reference/coledocument-class.md#onfilesendmail)

## <a name="see-also"></a>Voir aussi

[MAPI](mapi.md)
