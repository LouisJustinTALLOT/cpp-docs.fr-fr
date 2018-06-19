---
title: 'MFC : Utilisation de Classes de base de données avec des Documents et vues | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- documents [C++], database applications
- recordsets [C++], documents and views
- CRecordView class, using in database forms
- views [C++], database applications
- forms [C++], database applications
- record views [C++], form-based applications
- document/view architecture [C++], in databases
- database applications [C++], forms
- database classes [C++], MFC
- ODBC recordsets [C++], documents and views
- ODBC [C++], forms
ms.assetid: 83979974-fc63-46ac-b162-e8403a572e2c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fcaee376b53c1d592f02aafc830a35d72f64feeb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091866"
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC : utilisation de classes de bases de données avec des documents et des vues
Vous pouvez utiliser les classes de base de données MFC avec ou sans l’architecture document/vue. Cette rubrique met en évidence l’utilisation des documents et vues. Il explique :  
  
-   [Comment écrire une application basée sur le formulaire](#_core_writing_a_form.2d.based_application) à l’aide un `CRecordView` objet en tant que vue principale de votre document.  
  
-   [Comment utiliser des objets recordset dans vos documents et vues](#_core_using_recordsets_in_documents_and_views).  
  
-   [Autres considérations](#_core_other_factors).  
  
 Pour des alternatives, consultez [MFC : à l’aide de Classes de base de données sans document ni vue](../data/mfc-using-database-classes-without-documents-and-views.md).  
  
##  <a name="_core_writing_a_form.2d.based_application"></a> L’écriture d’une Application basée sur un formulaire  
 De nombreuses applications d’accès aux données sont basées sur les formulaires. L’interface utilisateur est un formulaire contenant des contrôles dans lesquels l’utilisateur examine, entre ou modifie des données. Pour rendre votre formulaire d’application en fonction, utilisez la classe `CRecordView`. Lorsque vous exécutez l’Assistant Application MFC et sélectionnez **ODBC** type de client sur le **prise en charge de la base de données** page, le projet utilise `CRecordView` pour la classe d’affichage.
  
 Dans une application basée sur le formulaire, chaque objet de vue de l’enregistrement stocke un pointeur vers un `CRecordset` objet. Mécanisme de l’infrastructure record field exchange (RFX) échange des données entre le jeu d’enregistrements et la source de données. Les données de la boîte de dialogue échangent mécanisme (DDX) échange des données entre les membres de données de champ de l’objet recordset et les contrôles du formulaire. `CRecordView` fournit également par défaut fonctions gestionnaires de commandes pour naviguer entre les enregistrements sur le formulaire.  
  
 Pour créer une application basée sur un formulaire avec l’Assistant application, consultez [création d’une Application MFC basée sur des formulaires](../mfc/reference/creating-a-forms-based-mfc-application.md) et [prise en charge de la base de données, Assistant Application MFC](../mfc/reference/database-support-mfc-application-wizard.md).  
  
 Pour obtenir une description détaillée des formulaires, consultez [vues des enregistrements](../data/record-views-mfc-data-access.md).  
  
##  <a name="_core_using_recordsets_in_documents_and_views"></a> À l’aide de jeux d’enregistrements dans des Documents et vues  
 De nombreuses applications simples basée sur formulaire n’avez pas besoin de documents. Si votre application est plus complexe, vous souhaitez probablement utiliser un document en tant que proxy pour la base de données, le stockage un `CDatabase` objet qui se connecte à la source de données. Sur les formulaires stockage généralement un pointeur vers un objet de jeu d’enregistrements dans la vue. D’autres types d’applications de base de données stockent des jeux d’enregistrements et `CDatabase` objet dans le document. Voici quelques possibilités d’utilisation de documents dans les applications de base de données :  
  
-   Si vous accédez à un jeu d’enregistrements dans un contexte local, créez un `CRecordset` de l’objet localement dans des fonctions membres du document ou de la vue, en fonction des besoins.  
  
     Déclarez un objet recordset comme une variable locale dans une fonction. Passer **NULL** au constructeur, ce qui entraîne le framework créer et ouvrir un fichier temporaire `CDatabase` objet pour vous. En guise d’alternative, passez un pointeur vers un `CDatabase` objet. Utiliser le jeu d’enregistrements dans la fonction et laissez-le d’être détruit automatiquement lors de la fermeture de la fonction.  
  
     Lorsque vous passez **NULL** à un constructeur de jeu d’enregistrements, l’infrastructure utilise les informations retournées par le jeu d’enregistrements `GetDefaultConnect` fonction membre pour créer un `CDatabase` de l’objet et l’ouvrir. Les Assistants implémentent `GetDefaultConnect` pour vous.  
  
-   Si vous accédez à un jeu d’enregistrements pendant la durée de vie de votre document, incorporez un ou plusieurs `CRecordset` objets dans votre document.  
  
     Construire les objets recordset lorsque vous initialisez le document ou en fonction des besoins. Vous pouvez écrire une fonction qui retourne un pointeur vers le recordset, s’il existe déjà, ou qui construit et ouvre le recordset, s’il n’existe pas encore. Fermez, supprimer et recréez le jeu d’enregistrements en fonction des besoins ou appeler son **Requery** fonction membre pour actualiser les enregistrements.  
  
-   Si vous accédez à une source de données pendant la durée de vie de votre document, incorporez un `CDatabase` de l’objet ou stocker un pointeur vers un `CDatabase` objet qu’il contient.  
  
     Le `CDatabase` objet gère une connexion à votre source de données. L’objet est généré automatiquement pendant la construction du document, et que vous appelez ses **ouvrir** fonction membre lorsque vous initialisez le document. Lorsque vous construisez des objets recordset dans des fonctions membres de document, vous passez un pointeur vers le document `CDatabase` objet. Cela associe chaque jeu d’enregistrements à sa source de données. L’objet de base de données est généralement détruit lors de la fermeture du document. Les objets recordset sont généralement détruits lorsqu’ils quittent la portée d’une fonction.  
  
##  <a name="_core_other_factors"></a> Autres facteurs  
 Sur les formulaires souvent ont toute utilisation du mécanisme de sérialisation de document de l’infrastructure, et vous souhaiterez peut-être supprimer, désactiver ou de remplacer le `New` et **ouvrir** des commandes sur le **fichier**menu. Consultez l’article [sérialisation : sérialisation et. Base de données d’entrée/sortie](../mfc/serialization-serialization-vs-database-input-output.md).  
  
 Vous pourriez également s’utiliser de nombreuses possibilités de l’interface utilisateur prises en charge par le framework. Par exemple, vous pouvez utiliser plusieurs `CRecordView` objets dans une fenêtre fractionnée, ouvrir plusieurs jeux d’enregistrements dans différentes plusieurs fenêtres enfants de l’interface (multidocument MDI) document et ainsi de suite.  
  
 Vous pouvez souhaiter implémenter l’impression de tout ce qui est visible, que ce soit un formulaire implémenté avec `CRecordView` ou autre chose. Comme les classes dérivées de `CFormView`, `CRecordView` ne prend pas en charge l’impression, mais vous pouvez remplacer le `OnPrint` fonction membre pour l’impression. Pour plus d’informations, consultez la classe [CFormView](../mfc/reference/cformview-class.md).  
  
 Vous pouvez utiliser du tout les documents et vues. Dans ce cas, consultez [MFC : à l’aide de Classes de base de données sans document ni vue](../data/mfc-using-database-classes-without-documents-and-views.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Les Classes de base de données MFC (.. / data/mfc-database-classes-odbc-and-dao.md)