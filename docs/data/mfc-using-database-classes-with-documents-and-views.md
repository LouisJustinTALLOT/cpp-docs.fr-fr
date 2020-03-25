---
title: 'MFC : utilisation de classes de bases de données avec des documents et des vues'
ms.date: 11/04/2016
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
ms.openlocfilehash: e2b073b20b9518667b43c30e7ee3199a84a3ad38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213380"
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC : utilisation de classes de bases de données avec des documents et des vues

Vous pouvez utiliser les classes de base de données MFC avec ou sans l’architecture document/vue. Cette rubrique met l’accent sur l’utilisation des documents et des vues. Elle explique les éléments suivants :

- [Comment écrire une application basée](#_core_writing_a_form.2d.based_application) sur un formulaire à l’aide d’un objet `CRecordView` en tant que vue principale de votre document.

- [Comment utiliser des objets Recordset dans vos documents et vues](#_core_using_recordsets_in_documents_and_views).

- [Autres considérations](#_core_other_factors).

Pour les autres solutions, consultez [MFC : utilisation de classes de bases de données sans document ni vue](../data/mfc-using-database-classes-without-documents-and-views.md).

##  <a name="writing-a-form-based-application"></a><a name="_core_writing_a_form.2d.based_application"></a>Écriture d’une application basée sur un formulaire

De nombreuses applications d’accès aux données sont basées sur des formulaires. L’interface utilisateur est un formulaire contenant des contrôles dans lesquels l’utilisateur examine, entre ou modifie des données. Pour que votre application soit basée sur un formulaire, utilisez la classe `CRecordView`. Lorsque vous exécutez l’Assistant Application MFC et sélectionnez type de client **ODBC** sur la page **prise en charge de base de données** , le projet utilise `CRecordView` pour la classe d’affichage.

Dans une application basée sur des formulaires, chaque objet de vue de l’enregistrement stocke un pointeur vers un objet `CRecordset`. Le mécanisme RFX (Record Field Exchange) de l’infrastructure échange des données entre le Recordset et la source de données. Le mécanisme DDX (Dialog Data Exchange) échange des données entre les membres de données de champ de l’objet Recordset et les contrôles du formulaire. `CRecordView` fournit également des fonctions de gestionnaire de commandes par défaut pour naviguer d’un enregistrement à un autre sur le formulaire.

Pour créer une application basée sur des formulaires à l’aide de l’Assistant Application, consultez [création d’une application MFC basée sur les formulaires](../mfc/reference/creating-a-forms-based-mfc-application.md) et [prise en charge des bases de données, Assistant Application MFC](../mfc/reference/database-support-mfc-application-wizard.md).

Pour une présentation complète des formulaires, consultez [vues des enregistrements](../data/record-views-mfc-data-access.md).

##  <a name="using-recordsets-in-documents-and-views"></a><a name="_core_using_recordsets_in_documents_and_views"></a>Utilisation de recordsets dans des documents et des vues

De nombreuses applications simples basées sur des formulaires n’ont pas besoin de documents. Si votre application est plus complexe, vous souhaiterez probablement utiliser un document comme proxy pour la base de données, en stockant un objet `CDatabase` qui se connecte à la source de données. Les applications basées sur les formulaires stockent généralement un pointeur vers un objet Recordset dans la vue. D’autres types d’applications de base de données stockent des jeux d’enregistrements et des `CDatabase` objet dans le document. Voici quelques possibilités d’utiliser des documents dans les applications de base de données :

- Si vous accédez à un Recordset dans un contexte local, créez un objet `CRecordset` localement dans les fonctions membres du document ou de la vue, si nécessaire.

   Déclarez un objet Recordset en tant que variable locale dans une fonction. Transmettez la valeur NULL au constructeur, ce qui amène l’infrastructure à créer et ouvrir un objet `CDatabase` temporaire pour vous. Vous pouvez également passer un pointeur vers un objet `CDatabase`. Utilisez le Recordset dans la fonction et laissez-le être détruit automatiquement lorsque la fonction se termine.

   Quand vous transmettez la valeur NULL à un constructeur Recordset, l’infrastructure utilise les informations retournées par la fonction membre `GetDefaultConnect` du Recordset pour créer un objet `CDatabase` et l’ouvrir. Les assistants implémentent `GetDefaultConnect` pour vous.

- Si vous accédez à un Recordset pendant la durée de vie de votre document, incorporez un ou plusieurs objets `CRecordset` dans votre document.

   Construisez les objets Recordset lorsque vous initialisez le document ou selon les besoins. Vous pouvez écrire une fonction qui retourne un pointeur vers le Recordset s’il existe déjà, ou construit et ouvre le Recordset s’il n’existe pas encore. Fermez, supprimez et recréez le Recordset si nécessaire, ou appelez sa fonction membre `Requery` pour actualiser les enregistrements.

- Si vous accédez à une source de données pendant la durée de vie de votre document, incorporez un objet `CDatabase` ou stockez-y un pointeur vers un objet `CDatabase`.

   L’objet `CDatabase` gère une connexion à votre source de données. L’objet est construit automatiquement pendant la construction du document, et vous appelez sa fonction membre `Open` lorsque vous initialisez le document. Lorsque vous construisez des objets Recordset dans des fonctions membres de document, vous transmettez un pointeur vers l’objet `CDatabase` du document. Cela associe chaque Recordset à sa source de données. L’objet de base de données est généralement détruit lorsque le document se ferme. Les objets Recordset sont généralement détruits lorsqu’ils quittent l’étendue d’une fonction.

##  <a name="other-factors"></a><a name="_core_other_factors"></a>Autres facteurs

Les applications basées sur les formulaires ne sont souvent pas utilisées pour le mécanisme de sérialisation de documents de l’infrastructure. vous pouvez donc supprimer, désactiver ou remplacer les commandes **nouveau** et **ouvrir** dans le menu **fichier** . Consultez l’article [sérialisation : sérialisation et entrées/sorties de base de données](../mfc/serialization-serialization-vs-database-input-output.md).

Vous pouvez également utiliser les nombreuses possibilités de l’interface utilisateur que l’infrastructure peut prendre en charge. Par exemple, vous pouvez utiliser plusieurs objets `CRecordView` dans une fenêtre fractionnée, ouvrir plusieurs recordsets dans différentes fenêtres enfants MDI (multiple document interface), et ainsi de suite.

Vous souhaiterez peut-être implémenter l’impression de tout ce qui se trouve dans votre affichage, qu’il s’agisse d’une forme implémentée avec `CRecordView` ou autre chose. Comme les classes dérivées de `CFormView`, `CRecordView` ne prend pas en charge l’impression, mais vous pouvez remplacer la fonction membre `OnPrint` pour permettre l’impression. Pour plus d’informations, consultez la classe [CFormView](../mfc/reference/cformview-class.md).

Il se peut que vous ne souhaitiez pas utiliser des documents et des vues. Dans ce cas, consultez [MFC : utilisation de classes de bases de données sans document ni vue](../data/mfc-using-database-classes-without-documents-and-views.md).

## <a name="see-also"></a>Voir aussi

[Classes de base de données MFC](../data/mfc-database-classes-odbc-and-dao.md)
