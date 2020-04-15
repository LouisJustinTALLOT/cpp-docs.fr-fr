---
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
ms.openlocfilehash: 3024f744407cf33c8dfad8a6f7af736e0f8061ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356999"
---
# <a name="mapi-support-in-mfc"></a>Prise en charge MAPI dans MFC

MFC fournit un support pour un sous-ensemble de l’interface du programme d’application de messagerie Microsoft (MAPI) en classe `CDocument`. Plus `CDocument` précisément, a des fonctions de membre qui déterminent si le support de messagerie est présent sur la machine de l’utilisateur final et, si oui, activer une commande De Courrier Envoyer dont l’ID de commande standard est ID_FILE_SEND_MAIL. La fonction de gestionnaire MFC pour cette commande permet à l'utilisateur d'envoyer un document via la messagerie électronique.

> [!TIP]
> Bien que MFC n'encapsule pas l'ensemble des fonctions MAPI, vous pouvez toujours appeler les fonctions MAPI directement, de la même manière que vous pouvez appeler les fonctions API Win32 directement à partir des programmes MFC.

L'activation de la commande Envoyer un message dans votre application est très simple. MFC fournit la mise en œuvre `CDocument`pour emballer un document (c’est-à-dire un objet dérivé) comme pièce jointe et l’envoyer par courrier. Cette pièce jointe est équivalente à une commande d'enregistrement de fichier qui stocke (sérialise) le contenu du document dans le message électronique. Cette implémentation appelle le client de messagerie sur l’ordinateur de l’utilisateur pour permettre à ce dernier d’adresser le message et d’y ajouter un objet et un texte. Les utilisateurs voient l'interface usuelle de leur application de messagerie usuelle. Cette fonctionnalité est fournie `CDocument` par deux `OnFileSendMail` `OnUpdateFileSendMail`fonctions membres: et .

L'interface MAPI doit lire le fichier pour envoyer la pièce jointe. Si l'application garde son fichier de données ouvert pendant un appel de fonction `OnFileSendMail`, le fichier doit être ouvert avec un mode de partage qui autorise plusieurs processus à y accéder.

> [!NOTE]
> Une version de substitution de `OnFileSendMail` pour la classe `COleDocument` traite correctement les documents composés.

#### <a name="to-implement-a-send-mail-command-with-mfc"></a>Pour implémenter une commande Envoyer un message avec MFC

1. Utilisez l'éditeur de menu de Visual C++ pour ajouter un élément de menu dont l'ID de commande est ID_FILE_SEND_MAIL.

   Cet ID de commande est fourni par le framework dans AFXRES.H. La commande peut être ajoutée à n’importe quel menu, mais elle est généralement ajoutée au menu **Fichier.**

1. Ajoutez manuellement le code suivant à la table des messages de votre document :

   [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/cpp/mapi-support-in-mfc_1.cpp)]

    > [!NOTE]
    >  Cette carte de message fonctionne `CDocument` pour `COleDocument` un document dérivé de l’un ou l’autre ou — il capte la classe de base correcte dans les deux cas, même si la carte de message est dans votre classe de document dérivée.

1. Construisez votre application.

Si la prise en charge de la messagerie est disponible, MFC active votre élément de menu avec `OnUpdateFileSendMail` et traite ensuite la commande avec `OnFileSendMail`. Si elle n'est pas disponible, MFC supprime automatiquement votre élément de menu afin que l'utilisateur ne le voit pas.

> [!TIP]
> Plutôt que d’ajouter manuellement des entrées de carte de message comme décrit précédemment, vous pouvez utiliser le [Class Class Wizard](reference/mfc-class-wizard.md) de classe pour cartographier les messages aux fonctions. Pour plus d’informations, voir [Messages de cartographie aux fonctions](../mfc/reference/mapping-messages-to-functions.md).

Pour obtenir de l’information connexe, consultez la vue d’ensemble [du MAPI.](../mfc/mapi.md)

Pour plus d’informations sur les `CDocument` fonctions des membres qui permettent MAPI, voir:

- [CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)

- [CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)

- [COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)

## <a name="see-also"></a>Voir aussi

[MAPI](../mfc/mapi.md)
