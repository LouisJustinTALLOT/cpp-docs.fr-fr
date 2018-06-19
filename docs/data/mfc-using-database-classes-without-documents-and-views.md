---
title: 'MFC : Utilisation de Classes de base de données sans document ni vue | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ba2e59b53524975f87e4ad7ffe99b9a4a3cc870d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093894"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC : utilisation de classes de bases de données sans document ni vue
Parfois, vous pouvez utiliser l’architecture document/vue de l’infrastructure dans vos applications de base de données. Cette rubrique explique :  
  
-   [Lorsque vous n’avez pas besoin d’utiliser des documents](#_core_when_you_don.92.t_need_documents) tels que de la sérialisation des documents.  
  
-   [Options de l’Assistant Application](#_core_appwizard_options_for_documents_and_views) pour prendre en charge des applications sans sérialisation et sans liées aux documents **fichier** tels que des commandes de menu **nouveau**, **ouvrir** , **Enregistrer**, et **enregistrer en tant que**.  
  
-   [Comment travailler avec une application qui utilise un document minimal](#_core_applications_with_minimal_documents).  
  
-   [Comment structurer une application sans document ni vue](#_core_applications_with_no_document).  
  
##  <a name="_core_when_you_don.92.t_need_documents"></a> Lorsque vous n’avez pas besoin des Documents  
 Certaines applications ont un concept distinct d’un document. Ces applications chargent généralement tout ou partie d’un fichier à partir du stockage en mémoire avec un **ouvrir le fichier** commande. Elles réécrivent le fichier mis à jour au stockage, à la fois avec un **l’enregistrement du fichier** ou **Enregistrer sous** commande. Ce que l’utilisateur voit est un fichier de données.  
  
 Toutefois, certaines catégories d’applications, ne nécessitent pas un document. Les applications de base de données fonctionnent en termes de transactions. L’application sélectionne des enregistrements à partir d’une base de données et les présente à l’utilisateur, souvent un à la fois. Ce que l’utilisateur voit est généralement un seul enregistrement actuel, qui peut être le seul en mémoire.  
  
 Si votre application ne requiert pas un document pour le stockage des données, vous pouvez vous passer de tout ou partie de l’architecture document/vue de l’infrastructure. Combien vous passer dépend de l’approche que vous préférez. Vous pouvez :  
  
-   Utiliser un document minimal comme emplacement pour stocker une connexion à votre source de données, mais avec des fonctionnalités de document normal telles que la sérialisation de distribution. Cela est utile lorsque vous souhaitez que plusieurs vues des données et que vous souhaitez synchroniser toutes les vues, mise à jour à la fois et ainsi de suite.  
  
-   Utiliser une fenêtre frame, dans laquelle vous dessinez directement, au lieu d’utiliser une vue. Dans ce cas, vous omettez le document et stockez les données ou les connexions de données dans l’objet fenêtre frame.  
  
##  <a name="_core_appwizard_options_for_documents_and_views"></a> Options de l’Assistant Application pour les Documents et vues  
 L’Assistant Application MFC a plusieurs options **sélectionnez prise en charge de la base de données**, qui sont répertoriées dans le tableau suivant. Si vous utilisez l’Assistant Application MFC pour créer une application, toutes ces options produisent des applications avec des documents et vues. Certaines options fournissent des documents et des vues qui omettent la fonction de document superflue. Pour plus d’informations, consultez [prise en charge de la base de données, Assistant Application MFC](../mfc/reference/database-support-mfc-application-wizard.md).  
  
|Option|Vue|Document|  
|------------|----------|--------------|  
|**Aucun**|Dérivée de `CView`.|Ne fournit aucune prise en charge de la base de données. Il s'agit de l'option par défaut.<br /><br /> Si vous sélectionnez le **prise en charge d’architecture Document/vue** option sur le [Type d’Application, Assistant Application MFC](../mfc/reference/application-type-mfc-application-wizard.md) page, vous obtenez prise en charge complète pour le document, y compris la sérialisation et `New`,  **Ouvrez**, **enregistrer**, et **enregistrer en tant que** des commandes sur le **fichier** menu. Consultez [Applications sans Document](#_core_applications_with_no_document).|  
|**Fichiers d’en-tête**|Dérivée de `CView`.|Fournit le niveau de prise en charge de la base de données de base pour votre application.<br /><br /> Inclut Afxdb.h. Ajoute des bibliothèques de liens, mais ne crée pas de classes spécifiques à la base de données. Vous pouvez créer des jeux d’enregistrements ultérieurement et les utiliser pour examiner et mettre à jour des enregistrements.|  
|**Vue de base de données sans prise en charge de fichier**|Dérivé de `CRecordView`|Fournit la prise en charge du document, mais aucune prise en charge de la sérialisation. Le document peut stocker le recordset et coordonner plusieurs vues ; ne prend pas en charge la sérialisation ou la `New`, **ouvrir**, **enregistrer**, et **Enregistrer sous** commandes. Consultez [Applications avec des Documents minimaux](#_core_applications_with_minimal_documents). Si vous incluez une vue de base de données, vous devez spécifier la source des données.<br /><br /> Inclut les fichiers d’en-tête de base de données, des bibliothèques de liens, une vue d’enregistrement et un jeu d’enregistrements. (Disponible uniquement pour les applications avec le **prise en charge d’architecture Document/vue** option est sélectionnée dans le [Type d’Application, Assistant Application MFC](../mfc/reference/application-type-mfc-application-wizard.md) page.)|  
|**Vue de base de données avec prise en charge de fichier**|Dérivé de `CRecordView`|Fournit une prise en charge complète pour le document, y compris la sérialisation et aux documents **fichier** commandes de menu. Les applications de base de données fonctionnent généralement par enregistrement plutôt que sur un fichier par fichier et n’avez pas besoin sérialisation. Toutefois, vous pouvez avoir une utilisation spéciale pour la sérialisation. Consultez [Applications avec des Documents minimaux](#_core_applications_with_minimal_documents). Si vous incluez une vue de base de données, vous devez spécifier la source des données.<br /><br /> Inclut les fichiers d’en-tête de base de données, des bibliothèques de liens, une vue d’enregistrement et un jeu d’enregistrements. (Disponible uniquement pour les applications avec le **prise en charge d’architecture Document/vue** option est sélectionnée dans le [Type d’Application, Assistant Application MFC](../mfc/reference/application-type-mfc-application-wizard.md) page.)|  
  
 Pour une présentation des alternatives à la sérialisation et les autres utilisations pour la sérialisation, consultez [sérialisation : sérialisation et. Base de données d’entrée/sortie](../mfc/serialization-serialization-vs-database-input-output.md).  
  
##  <a name="_core_applications_with_minimal_documents"></a> Applications avec des Documents minimaux  
 L’Assistant Application MFC propose deux options qui prennent en charge les applications d’accès aux données basées sur le formulaire. Chaque option crée un `CRecordView`-classe d’affichage et un document dérivés. Elles diffèrent dans qu’ils quittent hors du document.  
  
###  <a name="_core_a_document_without_file_support"></a> Document sans prise en charge de fichier  
 Sélectionnez l’option de base de données d’Assistant application **vue sans prise en charge des fichiers de base de données** si vous n’avez pas besoin de sérialisation de document. Le document utilisé aux fins utiles suivantes :  
  
-   Il s’agit d’un emplacement pratique pour stocker un `CRecordset` objet.  
  
     Cette utilisation correspond aux concepts de document ordinaires : le document stocke les données (ou, dans ce cas, un ensemble d’enregistrements) et la vue est une vue du document.  
  
-   Si votre application présente plusieurs vues (par exemple, plusieurs vues des enregistrements), un document prend en charge la coordination des vues.  
  
     Si plusieurs vues affichent les mêmes données, vous pouvez utiliser la `CDocument::UpdateAllViews` fonction membre pour coordonner les mises à jour de toutes les vues quand une vue modifie les données.  
  
 Vous utilisez généralement cette option pour les applications simples basées sur le formulaire. L’Assistant application prend en charge une structure pratique pour de telles applications automatiquement.  
  
###  <a name="_core_a_document_with_file_support"></a> Document avec prise en charge de fichier  
 Sélectionnez l’option de base de données d’Assistant application **vue avec prise en charge des fichiers de base de données** lorsque vous avez une utilisation alternative pour les documents liés **fichier** commandes de menu et de la sérialisation des documents. Pour la partie de l’accès aux données de votre programme, vous pouvez utiliser le document de la même façon comme décrit dans [Document sans prise en charge de fichier](#_core_a_document_without_file_support). Vous pouvez utiliser les capacités de sérialisation du document, par exemple, pour lire et écrire un document de profil utilisateur sérialisé qui stocke les préférences de l’utilisateur ou d’autres informations utiles. Pour plus d’informations, consultez [sérialisation : sérialisation et. Base de données d’entrée/sortie](../mfc/serialization-serialization-vs-database-input-output.md).  
  
 L’Assistant application prend en charge cette option, mais vous devez écrire le code qui sérialise le document. Stockez les informations sérialisées dans les membres de données de document.  
  
##  <a name="_core_applications_with_no_document"></a> Applications sans Document  
 Vous souhaiterez parfois écrire une application qui n’utilise pas de documents ou des vues. Sans document, vous stockez vos données (comme un `CRecordset` objet) dans votre classe de fenêtre frame ou de la classe de l’application. Des exigences supplémentaires dépendant de si l’application présente une interface utilisateur.  
  
###  <a name="_core_database_support_with_a_user_interface"></a> Prise en charge de la base de données avec une Interface utilisateur  
 Si vous avez une interface utilisateur (autre que, par exemple, une interface de ligne de commande de console), votre application Dessine directement dans la zone cliente de la fenêtre frame plutôt que dans une vue. Une telle application n’utilise pas `CRecordView`, `CFormView`, ou `CDialog` pour son interface utilisateur principale, mais il utilise normalement `CDialog` pour les boîtes de dialogue ordinaires.  
  
###  <a name="_core_writing_applications_without_documents"></a> Écriture d’Applications sans document  
 Étant donné que l’Assistant application ne prend pas en charge la création d’applications sans document, vous devez écrire votre propre `CWinApp`-classe dérivée et, si nécessaire, vous devez également créer un `CFrameWnd` ou `CMDIFrameWnd` classe. Substituer `CWinApp::InitInstance` et déclarer un objet de l’application en tant que :  
  
```  
CYourNameApp theApp;  
```  
  
 L’infrastructure fournit toujours le mécanisme de table des messages et de nombreuses autres fonctionnalités.  
  
###  <a name="_core_database_support_separate_from_the_user_interface"></a> Séparé de prise en charge de base de données à partir de l’Interface utilisateur  
 Certaines applications ont besoin d’aucune interface utilisateur ou uniquement un minimale. Par exemple, supposons que vous écrivez :  
  
-   Un objet d’accès aux données intermédiaire qui appellent d’autres applications (clients) pour un traitement spécial des données entre l’application et la source de données.  
  
-   Une application qui traite les données sans intervention de l’utilisateur, par exemple, une application qui déplace les données d’un format de base de données à un autre ou qui effectue des calculs et effectue des mises à jour par lots.  
  
 Parce qu’aucun document n’est propriétaire du `CRecordset` de l’objet, vous souhaiterez probablement stocker en tant que donnée membre incorporée dans votre `CWinApp`-classe d’application dérivée. Autres solutions possibles sont :  
  
-   Ne pas garder permanent `CRecordset` de l’objet du tout. Vous pouvez passer **NULL** aux constructeurs de classe de votre recordset. Dans ce cas, l’infrastructure crée un fichier temporaire `CDatabase` en utilisant les informations du jeu d’enregistrements de l’objet `GetDefaultConnect` fonction membre. Il s’agit de l’autre approche de la plus probable.  
  
-   Rendre le `CRecordset` une variable globale de l’objet. Cette variable doit être un pointeur vers un objet de jeu d’enregistrements que vous créez dynamiquement dans votre `CWinApp::InitInstance` remplacer. Cela évite de tentative de construction de l’objet avant l’initialisation de l’infrastructure.  
  
-   Comme vous le feriez dans le contexte d’un document ou d’une vue, à l’aide d’objets recordset. Créer des jeux d’enregistrements dans le membre de fonctions de votre application ou les objets de la fenêtre frame.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes de base de données MFC](../data/mfc-database-classes-odbc-and-dao.md)