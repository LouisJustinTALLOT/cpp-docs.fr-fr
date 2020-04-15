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
ms.openlocfilehash: c914a449b73e7da876d2e05b894c016b53881c3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360669"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC : utilisation de classes de bases de données sans document ni vue

Parfois, vous ne souhaitez peut-être pas utiliser l’architecture de document/vue du cadre dans vos applications de base de données. Cette rubrique répond aux questions suivantes :

- [Lorsque vous n’avez pas besoin d’utiliser](#_core_when_you_don.92.t_need_documents) des documents tels que la sérialisation des documents.

- [Options d’assistant d’application](#_core_appwizard_options_for_documents_and_views) pour prendre en charge les applications sans sérialisation et sans commandes de menu **de fichier** liées aux documents telles que **New**, **Open**, **Save**, et **Save As**.

- [Comment travailler avec une application qui utilise un document minimal](#_core_applications_with_minimal_documents).

- [Comment structurer une application sans document ni vue](#_core_applications_with_no_document).

## <a name="when-you-do-not-need-documents"></a><a name="_core_when_you_don.92.t_need_documents"></a>Lorsque vous n’avez pas besoin de documents

Certaines applications ont un concept distinct d’un document. Ces applications chargent généralement tout ou la plupart d’un fichier du stockage dans la mémoire avec une commande **De Fichier Open.** Ils rédigent le fichier mis à jour au stockage tout à la fois avec une **commande Enregistrer ou** enregistrer **comme** commande. Ce que l’utilisateur voit, c’est un fichier de données.

Toutefois, certaines catégories de demandes n’exigent pas de document. Les applications de base de données fonctionnent en termes de transactions. L’application sélectionne les enregistrements d’une base de données et les présente à l’utilisateur, souvent un à la fois. Ce que l’utilisateur voit est généralement un seul enregistrement en cours, qui pourrait être le seul dans la mémoire.

Si votre application n’exige pas de document pour stocker des données, vous pouvez vous passer d’une partie ou de la totalité de l’architecture de document/vue du cadre. Le montant dont vous vous dispensez dépend de l’approche que vous préférez. Vous pourriez :

- Utilisez un document minimal comme lieu pour stocker une connexion à votre source de données, mais dispensez-vous de fonctionnalités de documents normales telles que la sérialisation. Ceci est utile lorsque vous voulez plusieurs vues des données et que vous souhaitez synchroniser toutes les vues, les mettre à jour tous à la fois et ainsi de suite.

- Utilisez une fenêtre de cadre, dans laquelle vous dessinez directement, plutôt que d’utiliser une vue. Dans ce cas, vous ometez le document et stockez toutes les connexions de données ou de données dans l’objet de la fenêtre d’image.

## <a name="application-wizard-options-for-documents-and-views"></a><a name="_core_appwizard_options_for_documents_and_views"></a>Options d’assistant d’application pour les documents et les vues

L’assistant d’application MFC a plusieurs options dans **le support de base de données Select**, qui sont répertoriés dans le tableau suivant. Si vous utilisez l’assistant d’application MFC pour créer une application, toutes ces options produisent des applications avec des documents et des vues. Certaines options fournissent des documents et des points de vue qui ometent la fonctionnalité de document inutile. Pour plus d’informations, voir [Database Support, MFC Application Wizard](../mfc/reference/database-support-mfc-application-wizard.md).

|Option|Affichage|Document|
|------------|----------|--------------|
|**Aucun**|Dérivée de `CView`.|Fournit aucun support de base de données. Il s'agit de l'option par défaut.<br /><br /> Si vous sélectionnez **l’option de support d’architecture Document/vue** sur le [type d’application,](../mfc/reference/application-type-mfc-application-wizard.md) la page MFC Application Wizard, vous obtenez une prise en charge complète des documents, y compris la sérialisation et **la nouvelle**, **l’ouverture**, **l’enregistrement**et **l’enregistrement des** commandes sur le menu **Fichier.** Voir [les applications sans document](#_core_applications_with_no_document).|
|**Fichiers d’en-tête seulement**|Dérivée de `CView`.|Fournit le niveau de base de la prise en charge de base pour votre application.<br /><br /> Inclut Afxdb.h. Ajoute des bibliothèques de liens, mais ne crée pas de classes spécifiques à la base de données. Vous pouvez créer des enregistrements plus tard et les utiliser pour examiner et mettre à jour les enregistrements.|
|**Vue de base de données sans prise en charge de fichiers**|Dérivé de`CRecordView`|Fournit un support documentaire, mais pas de soutien à la sérialisation. Le document peut stocker l’enregistrement et coordonner plusieurs vues; ne prend pas en charge la sérialisation ou la **nouvelle**, **Open**, **Save**, et **Save As** commandes. Voir [les demandes avec des documents minimaux](#_core_applications_with_minimal_documents). Si vous incluez une vue de base de données, vous devez spécifier la source des données.<br /><br /> Inclut les fichiers d’en-tête de base de données, les bibliothèques de liaison, une vue d’enregistrement et un ensemble d’enregistrements. (Disponible uniquement pour les applications avec **l’option de support d’architecture Document/vue** sélectionnée sur le [type d’application,](../mfc/reference/application-type-mfc-application-wizard.md) page MFC Application Wizard.)|
|**Vue de base de données avec prise en charge de fichiers**|Dérivé de`CRecordView`|Fournit un support complet des documents, y compris la sérialisation et les commandes de menu **de fichiers** liées aux documents. Les applications de base de données fonctionnent généralement selon les dossiers plutôt que sur une base par fichier et n’ont donc pas besoin de sérialisation. Cependant, vous pourriez avoir une utilisation spéciale pour la sérialisation. Voir [les demandes avec des documents minimaux](#_core_applications_with_minimal_documents). Si vous incluez une vue de base de données, vous devez spécifier la source des données.<br /><br /> Inclut les fichiers d’en-tête de base de données, les bibliothèques de liaison, une vue d’enregistrement et un ensemble d’enregistrements. (Disponible uniquement pour les applications avec **l’option de support d’architecture Document/vue** sélectionnée sur le [type d’application,](../mfc/reference/application-type-mfc-application-wizard.md) page MFC Application Wizard.)|

Pour une discussion sur les alternatives à la sérialisation et les utilisations alternatives à la sérialisation, voir [Serialization: Serialization vs Database Input/Output](../mfc/serialization-serialization-vs-database-input-output.md).

## <a name="applications-with-minimal-documents"></a><a name="_core_applications_with_minimal_documents"></a>Applications avec des documents minimaux

L’assistant d’application MFC dispose de deux options qui prennent en charge les applications d’accès aux données basées sur les formulaires. Chaque option `CRecordView`crée une classe de vue dérivée et un document. Ils diffèrent dans ce qu’ils laissent de côté du document.

### <a name="document-without-file-support"></a><a name="_core_a_document_without_file_support"></a>Document sans soutien de fichier

Sélectionnez l’option de base de données d’assistants d’application **Database view sans prise en charge** de fichiers si vous n’avez pas besoin de sérialisation de documents. Le document sert les fins utiles suivantes :

- C’est un endroit `CRecordset` pratique pour stocker un objet.

   Cette utilisation est parallèle aux concepts de documents ordinaires : le document stocke les données (ou, dans ce cas, un ensemble d’enregistrements) et la vue est une vue du document.

- Si votre application présente plusieurs points de vue (tels que plusieurs vues d’enregistrement), un document prend en charge la coordination des points de vue.

   Si plusieurs vues affichent les mêmes `CDocument::UpdateAllViews` données, vous pouvez utiliser la fonction membre pour coordonner les mises à jour de toutes les vues lorsque n’importe quelle vue modifie les données.

Vous utilisez habituellement cette option pour des applications simples basées sur des formulaires. L’assistant d’application prend en charge automatiquement une structure pratique pour de telles applications.

### <a name="document-with-file-support"></a><a name="_core_a_document_with_file_support"></a>Document avec support de fichiers

Sélectionnez l’option de base de données d’assistants d’application Vue de base de données **avec prise en charge de fichiers** lorsque vous avez une autre utilisation pour les commandes de menu de **fichiers** liées au document et la sérialisation des documents. Pour la partie accès aux données de votre programme, vous pouvez utiliser le document de la même manière que décrit dans [Document Sans support de fichier](#_core_a_document_without_file_support). Vous pouvez utiliser la capacité de sérialisation du document, par exemple, pour lire et écrire un document de profil d’utilisateur sérialisé qui stocke les préférences de l’utilisateur ou d’autres informations utiles. Pour plus d’idées, voir [Serialization: Serialization vs Database Input/Output](../mfc/serialization-serialization-vs-database-input-output.md).

L’assistant d’application prend en charge cette option, mais vous devez écrire le code qui sérialisse le document. Stockez les informations sérialisées dans les membres des données documentaires.

## <a name="applications-with-no-document"></a><a name="_core_applications_with_no_document"></a>Applications sans document

Vous pouvez parfois écrire une application qui n’utilise pas de documents ou de vues. Sans documents, vous stockez vos `CRecordset` données (comme un objet) dans votre classe de fenêtre de cadre ou dans votre classe de demande. Toute exigence supplémentaire dépend de la question de savoir si l’application présente une interface utilisateur.

### <a name="database-support-with-a-user-interface"></a><a name="_core_database_support_with_a_user_interface"></a>Support de base de données avec une interface utilisateur

Si vous disposez d’une interface utilisateur (autre que, par exemple, d’une interface de ligne de commande console), votre application s’insurger directement dans la zone client de la fenêtre de cadre plutôt que dans une vue. Une telle application `CRecordView`n’utilise pas, `CFormView`, ou `CDialog` pour son `CDialog` interface utilisateur principale, mais il utilise normalement pour les dialogues ordinaires.

### <a name="writing-applications-without-documents"></a><a name="_core_writing_applications_without_documents"></a>Rédaction d’applications sans documents

Étant donné que l’assistant d’application ne prend `CWinApp`pas en charge la création `CFrameWnd` d’applications sans documents, vous devez écrire votre propre classe dérivée et, si nécessaire, créer un ou `CMDIFrameWnd` une classe. Remplacer `CWinApp::InitInstance` et déclarer un objet d’application comme :

```cpp
CYourNameApp theApp;
```

Le cadre fournit toujours le mécanisme de carte de message et de nombreuses autres fonctionnalités.

### <a name="database-support-separate-from-the-user-interface"></a><a name="_core_database_support_separate_from_the_user_interface"></a>Support de base de données Séparé de l’interface utilisateur

Certaines applications n’ont pas besoin d’interface utilisateur ou seulement d’une interface minimale. Supposons, par exemple, que vous écriviez :

- Un objet intermédiaire d’accès aux données que d’autres applications (clients) appellent pour un traitement spécial des données entre l’application et la source de données.

- Une application qui traite les données sans intervention de l’utilisateur, comme une application qui déplace les données d’un format de base de données à une autre ou une qui effectue des calculs et effectue des mises à jour par lots.

Étant donné qu’aucun document n’est propriétaire de l’objet, vous souhaitez probablement le `CRecordset` stocker en tant que membre de données intégrée dans votre `CWinApp`classe d’application dérivée. Les solutions de rechange comprennent :

- Ne pas `CRecordset` garder un objet permanent du tout. Vous pouvez passer NULL à vos constructeurs de classe de records. Dans ce cas, le `CDatabase` cadre crée un objet temporaire `GetDefaultConnect` en utilisant les informations dans la fonction membre du document. Il s’agit de l’approche alternative la plus probable.

- Faire `CRecordset` de l’objet une variable globale. Cette variable doit être un pointeur vers un objet `CWinApp::InitInstance` de l’ensemble d’enregistrements que vous créez dynamiquement dans votre remplacement. Cela évite de tenter de construire l’objet avant que le cadre ne soit parasécé.

- Utilisation d’objets d’enregistrement comme vous le feriez dans le contexte d’un document ou d’une vue. Créez des enregistrements dans les fonctions membres de votre application ou de vos objets de fenêtre de cadre.

## <a name="see-also"></a>Voir aussi

[Classes de base de données MFC](../data/mfc-database-classes-odbc-and-dao.md)
