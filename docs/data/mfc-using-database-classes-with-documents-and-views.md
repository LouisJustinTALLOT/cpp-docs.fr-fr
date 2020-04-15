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
ms.openlocfilehash: 9e071e0cc25492073cd74ed517284476b6e49ef8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368903"
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC : utilisation de classes de bases de données avec des documents et des vues

Vous pouvez utiliser les classes de base de données MFC avec ou sans l’architecture de document/vue. Ce sujet met l’accent sur le travail avec des documents et des points de vue. Il explique:

- [Comment écrire une application basée sur un formulaire à](#_core_writing_a_form.2d.based_application) l’aide d’un `CRecordView` objet comme vue principale sur votre document.

- [Comment utiliser des objets de la fiche dans vos documents et vues](#_core_using_recordsets_in_documents_and_views).

- [Autres considérations](#_core_other_factors).

Pour trouver des solutions de rechange, voir [MFC: Using Database Classes Without Documents and Views](../data/mfc-using-database-classes-without-documents-and-views.md).

## <a name="writing-a-form-based-application"></a><a name="_core_writing_a_form.2d.based_application"></a>Rédaction d’une application basée sur les formulaires

De nombreuses applications d’accès aux données sont basées sur des formulaires. L’interface utilisateur est un formulaire contenant des contrôles dans lequel l’utilisateur examine, entre ou modifie des données. Pour faire en sorte que `CRecordView`votre formulaire de demande soit basé, utilisez la classe . Lorsque vous exécutez l’assistant d’application MFC et sélectionnez le `CRecordView` type de client **ODBC** sur la page de support de base de **données,** le projet est destiné à la classe de vue.

Dans une application basée sur la forme, chaque `CRecordset` objet de vue d’enregistrement stocke un pointeur vers un objet. Le mécanisme d’échange de terrain record (RFX) du cadre échange des données entre l’enregistrement et la source de données. Le mécanisme d’échange de données de dialogue (DDX) échange des données entre les membres des données sur le terrain de l’objet de l’enregistrement et les contrôles sur le formulaire. `CRecordView`fournit également des fonctions de gestionnaire de commande par défaut pour naviguer d’enregistrement en enregistrement sur le formulaire.

Pour créer une application basée sur un formulaire avec l’assistant d’application, voir [Créer une application MFC basée sur les formulaires](../mfc/reference/creating-a-forms-based-mfc-application.md) et [le support de base de données, MFC Application Wizard](../mfc/reference/database-support-mfc-application-wizard.md).

Pour une discussion complète des formulaires, voir [Vues d’enregistrement](../data/record-views-mfc-data-access.md).

## <a name="using-recordsets-in-documents-and-views"></a><a name="_core_using_recordsets_in_documents_and_views"></a>Utilisation d’enregistrements dans documents et vues

De nombreuses applications simples basées sur des formulaires n’ont pas besoin de documents. Si votre application est plus complexe, vous souhaitez probablement utiliser un `CDatabase` document comme proxy pour la base de données, en stockant un objet qui se connecte à la source de données. Les applications basées sur les formulaires stockent généralement un pointeur sur un objet de recordet dans la vue. D’autres types d’applications `CDatabase` de base de données stockent des enregistrements et des objets dans le document. Voici quelques possibilités d’utilisation de documents dans les applications de base de données :

- Si vous accédez à un ensemble d’enregistrements dans un contexte local, créez un `CRecordset` objet localement dans les fonctions membres du document ou de la vue, au besoin.

   Déclarez un objet de recordet comme variable locale dans une fonction. Passez NULL au constructeur, ce qui provoque la création `CDatabase` et l’ouverture d’un objet temporaire pour vous. Comme alternative, passez un pointeur à un `CDatabase` objet. Utilisez l’enregistrement dans la fonction et laissez-le être détruit automatiquement lorsque la fonction sort.

   Lorsque vous passez NULL à un constructeur de documents, le cadre `GetDefaultConnect` utilise les informations `CDatabase` retournées par la fonction membre du document pour créer un objet et l’ouvrir. Les sorciers `GetDefaultConnect` mettent en œuvre pour vous.

- Si vous accédez à un ensemble d’enregistrements pendant la `CRecordset` durée de vie de votre document, intégrez un ou plusieurs objets dans votre document.

   Construisez les objets de l’enregistrement lorsque vous parasasez le document ou au besoin. Vous pouvez écrire une fonction qui renvoie un pointeur à l’enregistrement s’il existe déjà ou construit et ouvre le recordet si elle n’existe pas encore. Fermez, supprimez et recréez le `Requery` dossier au besoin, ou appelez sa fonction de membre pour actualiser les enregistrements.

- Si vous accédez à une source de données pendant `CDatabase` la durée de `CDatabase` vie de votre document, intégrez un objet ou stockez un pointeur vers un objet qui s’y trouve.

   L’objet `CDatabase` gère une connexion à votre source de données. L’objet est construit automatiquement pendant la `Open` construction de documents, et vous appelez sa fonction de membre lorsque vous initialisez le document. Lorsque vous construisez des objets d’enregistrement dans les fonctions `CDatabase` des membres du document, vous passez un pointeur à l’objet du document. Cela associe chaque ensemble d’enregistrements à sa source de données. L’objet de base de données est généralement détruit lorsque le document se ferme. Les objets de l’enregistrement sont généralement détruits lorsqu’ils sortent de la portée d’une fonction.

## <a name="other-factors"></a><a name="_core_other_factors"></a>Autres facteurs

Souvent, les applications basées sur les formulaires n’ont aucune utilité pour le mécanisme de sérialisation des documents du cadre, de sorte que vous voudrez peut-être supprimer, désactiver ou remplacer les commandes **Nouvelles** et **Ouvertes** sur le menu **Fichier.** Voir l’article [Serialization: Serialization vs Database Input/Output](../mfc/serialization-serialization-vs-database-input-output.md).

Vous pouvez également utiliser les nombreuses possibilités d’interface utilisateur que le cadre peut prendre en charge. Par exemple, vous `CRecordView` pouvez utiliser plusieurs objets dans une fenêtre de splitter, ouvrir plusieurs enregistrements dans différentes fenêtres d’enfant à interface de document multiple (MDI), et ainsi de suite.

Vous voudrez peut-être implémenter l’impression de tout `CRecordView` ce qui est à votre avis, qu’il s’agisse d’un formulaire mis en œuvre avec ou autre chose. Comme les `CFormView`classes `CRecordView` dérivées de , ne prend `OnPrint` pas en charge l’impression, mais vous pouvez remplacer la fonction membre pour permettre l’impression. Pour plus d’informations, voir classe [CFormView](../mfc/reference/cformview-class.md).

Vous ne voudrez peut-être pas utiliser des documents et des points de vue du tout. Dans ce cas, voir [MFC: Using Database Classes Without Documents and Views](../data/mfc-using-database-classes-without-documents-and-views.md).

## <a name="see-also"></a>Voir aussi

[Classes de base de données MFC](../data/mfc-database-classes-odbc-and-dao.md)
