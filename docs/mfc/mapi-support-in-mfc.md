---
title: Prise en charge MAPI dans MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, MAPI support
- MAPI support in MFC
- CDocument class [MFC], and MAPI
- OnUpdateFileSendMail method [MFC]
- MAPI, MFC
- OnFileSendMail method [MFC]
ms.assetid: cafbecb1-0427-4077-b4b8-159bae5b49b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e5d6498d1ecb20b47070cb26bf1a9d732340e266
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349660"
---
# <a name="mapi-support-in-mfc"></a>Prise en charge MAPI dans MFC
MFC prend en charge un sous-ensemble de la Microsoft programme Interface MAPI (Messaging Application) dans la classe **CDocument**. Plus précisément, **CDocument** dispose de fonctions membres qui déterminent si la prise en charge de la messagerie est présent sur l’ordinateur de l’utilisateur final et, dans ce cas, activer une commande Envoyer un message dont l’ID de commande standard est **ID_FILE_SEND_MAIL**. La fonction de gestionnaire MFC pour cette commande permet à l'utilisateur d'envoyer un document via la messagerie électronique.  
  
> [!TIP]
>  Bien que MFC n'encapsule pas l'ensemble des fonctions MAPI, vous pouvez toujours appeler les fonctions MAPI directement, de la même manière que vous pouvez appeler les fonctions API Win32 directement à partir des programmes MFC.  
  
 L'activation de la commande Envoyer un message dans votre application est très simple. MFC fournit l’implémentation pour empaqueter un document (autrement dit, un **CDocument**-objet dérivé) en tant que pièce jointe et l’envoyer en tant que courrier. Cette pièce jointe est équivalente à une commande d'enregistrement de fichier qui stocke (sérialise) le contenu du document dans le message électronique. Cette implémentation appelle le client de messagerie sur l’ordinateur de l’utilisateur pour permettre à ce dernier d’adresser le message et d’y ajouter un objet et un texte. Les utilisateurs voient l'interface usuelle de leur application de messagerie usuelle. Cette fonctionnalité est fournie par deux **CDocument** fonctions membres : `OnFileSendMail` et `OnUpdateFileSendMail`.  
  
 L'interface MAPI doit lire le fichier pour envoyer la pièce jointe. Si l'application garde son fichier de données ouvert pendant un appel de fonction `OnFileSendMail`, le fichier doit être ouvert avec un mode de partage qui autorise plusieurs processus à y accéder.  
  
> [!NOTE]
>  Une version de substitution de `OnFileSendMail` pour la classe `COleDocument` traite correctement les documents composés.  
  
#### <a name="to-implement-a-send-mail-command-with-mfc"></a>Pour implémenter une commande Envoyer un message avec MFC  
  
1.  Utilisez l’éditeur de menus Visual C++ pour ajouter un élément de menu dont l’ID de commande est **ID_FILE_SEND_MAIL**.  
  
     Cet ID de commande est fourni par le framework dans AFXRES.H. La commande peut être ajoutée à n’importe quel menu, mais elle est généralement ajoutée à la **fichier** menu.  
  
2.  Ajoutez manuellement le code suivant à la table des messages de votre document :  
  
     [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/cpp/mapi-support-in-mfc_1.cpp)]  
  
    > [!NOTE]
    >  Cette table des messages fonctionne pour un document dérivé **CDocument** ou **COleDocument** , elle sélectionne la classe de base dans les deux cas, même si la table des messages se trouve dans votre classe de document dérivée.  
  
3.  Générez votre application.  
  
 Si la prise en charge de la messagerie est disponible, MFC active votre élément de menu avec `OnUpdateFileSendMail` et traite ensuite la commande avec `OnFileSendMail`. Si elle n'est pas disponible, MFC supprime automatiquement votre élément de menu afin que l'utilisateur ne le voit pas.  
  
> [!TIP]
>  Au lieu d'ajouter manuellement des entrées de la table des messages comme décrit précédemment, vous pouvez utiliser la fenêtre Propriétés de la classe pour mapper les messages à des fonctions. Pour plus d’informations, consultez [mappage de Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md).  
  
 Pour plus d’informations, consultez la [MAPI](../mfc/mapi.md) vue d’ensemble.  
  
 Pour plus d’informations sur la **CDocument** fonctions membres qui activent l’interface MAPI, consultez :  
  
-   [CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)  
  
-   [CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)  
  
-   [COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)  
  
## <a name="see-also"></a>Voir aussi  
 [MAPI](../mfc/mapi.md)

