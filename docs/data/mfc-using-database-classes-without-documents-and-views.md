---
title: 'MFC : utilisation de classes de bases de données sans document ni vue'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC applications [C++], without views
- documents [C++], applications without
- ODBC applications [C++]
- document/view architecture [C++], in databases
- files [C++], MFC
- database classes [C++], MFC
- CRecordView class, using in database applications
- database applications [C++], without views
- database applications [C++], application wizard options
- application wizards [C++], creating database applications
- ODBC [C++], file support in database applications
- ODBC applications [C++], without documents
- database applications [C++], without documents
- user interface [C++], drawing information
ms.assetid: 15bf52d4-91cf-4b1d-8b37-87c3ae70123a
ms.openlocfilehash: 57a7abd89bc9bfb465912a35c21f9780668f4466
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213354"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC : utilisation de classes de bases de données sans document ni vue

Il peut arriver que vous ne souhaitiez pas utiliser l’architecture document/vue de l’infrastructure dans vos applications de base de données. Cette rubrique explique :

- [Lorsque vous n’avez pas besoin d’utiliser des documents](#_core_when_you_don.92.t_need_documents) tels que la sérialisation de document.

- [Options de l’Assistant Application](#_core_appwizard_options_for_documents_and_views) pour prendre en charge les applications sans sérialisation et sans commandes de menu de **fichier** liées aux documents telles que **nouveau**, **ouvrir**, **Enregistrer**et **Enregistrer sous**.

- [Comment utiliser une application qui utilise un document minimal](#_core_applications_with_minimal_documents).

- [Comment structurer une application sans document ni vue](#_core_applications_with_no_document).

##  <a name="when-you-do-not-need-documents"></a><a name="_core_when_you_don.92.t_need_documents"></a>Si vous n’avez pas besoin de documents

Certaines applications ont un concept distinct d’un document. Ces applications chargent généralement la totalité ou la majeure partie d’un fichier à partir du stockage en mémoire à l’aide d’une commande **fichier ouvrir** . Ils réécrivent le fichier mis à jour dans le stockage en une seule fois à l’aide d’une commande **fichier enregistrer** ou **Enregistrer sous** . Ce que voit l’utilisateur est un fichier de données.

Toutefois, certaines catégories d’applications ne nécessitent pas de document. Les applications de base de données fonctionnent en termes de transactions. L’application sélectionne des enregistrements à partir d’une base de données et les présente à l’utilisateur, souvent l’un après l’autre. Ce que voit l’utilisateur est généralement un enregistrement actif unique, qui peut être le seul en mémoire.

Si votre application ne nécessite pas de document pour le stockage des données, vous pouvez la distribuer avec tout ou partie de l’architecture document/vue de l’infrastructure. Le niveau de distribution dépend de l’approche que vous préférez. Vous pouvez :

- Utilisez un document minimal comme emplacement pour stocker une connexion à votre source de données, mais distribuez avec des fonctionnalités de document normales, telles que la sérialisation. Cela est utile lorsque vous souhaitez plusieurs vues des données et que vous souhaitez synchroniser toutes les vues, en les mettant à jour en même temps, et ainsi de suite.

- Utilisez une fenêtre frame, dans laquelle vous dessinez directement, plutôt que d’utiliser une vue. Dans ce cas, vous omettez le document et stockez les données ou les connexions de données dans l’objet de fenêtre frame.

##  <a name="application-wizard-options-for-documents-and-views"></a><a name="_core_appwizard_options_for_documents_and_views"></a>Options de l’Assistant application pour les documents et les vues

L’Assistant Application MFC offre plusieurs options dans la **prise en charge des bases de données SELECT**, qui sont répertoriées dans le tableau suivant. Si vous utilisez l’Assistant Application MFC pour créer une application, toutes ces options produisent des applications avec des documents et des vues. Certaines options fournissent des documents et des vues qui omettent les fonctionnalités de document inutiles. Pour plus d’informations, consultez [prise en charge des bases de données, Assistant Application MFC](../mfc/reference/database-support-mfc-application-wizard.md).

|Option|Affichage|Document|
|------------|----------|--------------|
|**Aucun**|Dérivée de `CView`.|Ne fournit aucune prise en charge de base de données. Il s'agit de l'option par défaut.<br /><br /> Si vous sélectionnez l’option **prise en charge de l’architecture document/vue** dans la page [type d’application, Assistant Application MFC](../mfc/reference/application-type-mfc-application-wizard.md) , vous bénéficiez d’une prise en charge complète des documents, notamment la sérialisation et les commandes **nouveau**, **ouvrir**, **Enregistrer**et **Enregistrer sous** dans le menu **fichier** . Consultez [applications sans document](#_core_applications_with_no_document).|
|**Fichiers d’en-tête uniquement**|Dérivée de `CView`.|Fournit le niveau de base de la prise en charge de base de données pour votre application.<br /><br /> Comprend AFXDB. h. Ajoute des bibliothèques de liens, mais ne crée pas de classes spécifiques à la base de données. Vous pouvez créer des jeux d’enregistrements ultérieurement et les utiliser pour examiner et mettre à jour des enregistrements.|
|**Vue de base de données sans prise en charge des fichiers**|Dérivée de `CRecordView`|Fournit la prise en charge des documents, mais sans prise en charge de la sérialisation. Le document peut stocker un Recordset et coordonner plusieurs vues ; ne prend pas en charge la sérialisation ou les commandes **nouveau**, **ouvrir**, **Enregistrer**et **Enregistrer sous** . Consultez [applications avec des documents minimaux](#_core_applications_with_minimal_documents). Si vous incluez une vue de base de données, vous devez spécifier la source des données.<br /><br /> Comprend les fichiers d’en-tête de base de données, les bibliothèques de liens, une vue d’enregistrement et un Recordset. (Disponible uniquement pour les applications avec l’option **prise en charge de l’architecture document/vue** sélectionnée dans la page [type d’application, Assistant Application MFC](../mfc/reference/application-type-mfc-application-wizard.md) .)|
|**Vue de base de données avec prise en charge des fichiers**|Dérivée de `CRecordView`|Fournit une prise en charge complète des documents, y compris la sérialisation et les commandes de menu **fichier** relatives aux documents. En règle générale, les applications de base de données opèrent sur la base d’un enregistrement plutôt que sur une base par fichier et n’ont donc pas besoin d’être sérialisées. Toutefois, vous pouvez avoir une utilisation spéciale pour la sérialisation. Consultez [applications avec des documents minimaux](#_core_applications_with_minimal_documents). Si vous incluez une vue de base de données, vous devez spécifier la source des données.<br /><br /> Comprend les fichiers d’en-tête de base de données, les bibliothèques de liens, une vue d’enregistrement et un Recordset. (Disponible uniquement pour les applications avec l’option **prise en charge de l’architecture document/vue** sélectionnée dans la page [type d’application, Assistant Application MFC](../mfc/reference/application-type-mfc-application-wizard.md) .)|

Pour plus d’informations sur les alternatives à la sérialisation et les autres utilisations pour la sérialisation, consultez [sérialisation : sérialisation et entrées/sorties de base de données](../mfc/serialization-serialization-vs-database-input-output.md).

##  <a name="applications-with-minimal-documents"></a><a name="_core_applications_with_minimal_documents"></a>Applications avec des documents minimaux

L’Assistant Application MFC a deux options qui prennent en charge les applications d’accès aux données basées sur les formulaires. Chaque option crée une classe d’affichage dérivée de `CRecordView`et un document. Ils diffèrent dans ce qu’ils quittent du document.

###  <a name="document-without-file-support"></a><a name="_core_a_document_without_file_support"></a>Document sans prise en charge des fichiers

Sélectionnez l’option de base de données de l’Assistant application **vue de base de données sans prise en charge des fichiers** si vous n’avez pas besoin de sérialisation de documents. Le document remplit les fonctions suivantes :

- Il s’agit d’un emplacement pratique pour stocker un objet `CRecordset`.

   Cette utilisation est parallèle aux concepts de document ordinaires : le document stocke les données (ou, dans ce cas, un ensemble d’enregistrements) et la vue est une vue du document.

- Si votre application présente plusieurs vues (telles que plusieurs vues d’enregistrement), un document prend en charge la coordination des vues.

   Si plusieurs vues affichent les mêmes données, vous pouvez utiliser la fonction membre `CDocument::UpdateAllViews` pour coordonner les mises à jour de toutes les vues quand une vue modifie les données.

Vous utilisez généralement cette option pour les applications à base de formulaires simples. L’Assistant application prend en charge une structure pratique pour ces applications automatiquement.

###  <a name="document-with-file-support"></a><a name="_core_a_document_with_file_support"></a>Document avec prise en charge des fichiers

Sélectionnez l’option de base de données de l’Assistant application **vue de base de données avec prise en charge des fichiers** lorsque vous avez une autre utilisation pour les commandes de menu **fichier** liées aux documents et la sérialisation de documents. Pour la partie accès aux données de votre programme, vous pouvez utiliser le document de la même façon que décrit dans [document sans prise en charge des fichiers](#_core_a_document_without_file_support). Vous pouvez utiliser la fonction de sérialisation du document, par exemple, pour lire et écrire un document de profil utilisateur sérialisé qui stocke les préférences de l’utilisateur ou d’autres informations utiles. Pour plus d’informations, consultez [sérialisation : sérialisation et entrées/sorties de base de données](../mfc/serialization-serialization-vs-database-input-output.md).

L’Assistant application prend en charge cette option, mais vous devez écrire le code qui sérialise le document. Stocke les informations sérialisées dans les membres de données de document.

##  <a name="applications-with-no-document"></a><a name="_core_applications_with_no_document"></a>Applications sans document

Vous pouvez parfois souhaiter écrire une application qui n’utilise pas de documents ou de vues. Sans documents, vous stockez vos données (par exemple, un objet `CRecordset`) dans votre classe de fenêtre frame ou votre classe d’application. Toutes les exigences supplémentaires varient selon que l’application présente une interface utilisateur.

###  <a name="database-support-with-a-user-interface"></a><a name="_core_database_support_with_a_user_interface"></a>Prise en charge des bases de données avec une interface utilisateur

Si vous disposez d’une interface utilisateur (autre que, par exemple, une interface de ligne de commande de la console), votre application crée directement dans la zone cliente de la fenêtre frame plutôt que dans une vue. Une telle application n’utilise pas `CRecordView`, `CFormView`ou `CDialog` pour son interface utilisateur principale, mais elle utilise généralement des `CDialog` pour les boîtes de dialogue ordinaires.

###  <a name="writing-applications-without-documents"></a><a name="_core_writing_applications_without_documents"></a>Écriture d’applications sans documents

Étant donné que l’Assistant application ne prend pas en charge la création d’applications sans documents, vous devez écrire votre propre classe dérivée de `CWinApp`et, si nécessaire, créer également une classe `CFrameWnd` ou `CMDIFrameWnd`. Remplacez `CWinApp::InitInstance` et déclarez un objet d’application comme suit :

```cpp
CYourNameApp theApp;
```

L’infrastructure fournit toujours le mécanisme de la table des messages et de nombreuses autres fonctionnalités.

###  <a name="database-support-separate-from-the-user-interface"></a><a name="_core_database_support_separate_from_the_user_interface"></a>Prise en charge des bases de données distinctes de l’interface utilisateur

Certaines applications n’ont pas besoin d’une interface utilisateur ou d’une seule minimale. Par exemple, supposons que vous écrivez :

- Objet intermédiaire d’accès aux données que les autres applications (clients) appellent pour le traitement spécial des données entre l’application et la source de données.

- Application qui traite des données sans intervention de l’utilisateur, telle qu’une application qui déplace des données d’un format de base de données vers un autre ou qui effectue des calculs et effectue des mises à jour par lots.

Étant donné qu’aucun document n’est propriétaire de l’objet `CRecordset`, vous souhaiterez probablement le stocker en tant que membre de données incorporé dans votre classe d’application dérivée de `CWinApp`. Les alternatives sont les suivantes :

- Ne pas conserver un objet `CRecordset` permanent. Vous pouvez passer la valeur NULL aux constructeurs de la classe Recordset. Dans ce cas, l’infrastructure crée un objet `CDatabase` temporaire à l’aide des informations contenues dans la fonction membre `GetDefaultConnect` du Recordset. Il s’agit de l’approche alternative la plus probable.

- Définition de l’objet `CRecordset` en tant que variable globale. Cette variable doit être un pointeur vers un objet Recordset que vous créez dynamiquement dans votre `CWinApp::InitInstance` remplacement. Cela évite toute tentative de construction de l’objet avant l’initialisation de l’infrastructure.

- Utilisation d’objets Recordset comme vous le feriez dans le contexte d’un document ou d’une vue. Créez des jeux d’enregistrements dans les fonctions membres de votre application ou des objets de fenêtre frame.

## <a name="see-also"></a>Voir aussi

[Classes de base de données MFC](../data/mfc-database-classes-odbc-and-dao.md)
