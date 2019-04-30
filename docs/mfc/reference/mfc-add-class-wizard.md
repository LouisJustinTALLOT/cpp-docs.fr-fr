---
title: Assistant Ajouter une classe MFC
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.mfc.simple.overview
helpviewer_keywords:
- MFC Add Class Wizard
- wizards [MFC]
ms.assetid: ad3b0989-d307-43b2-9417-3f9a78889024
ms.openlocfilehash: fa9b947ae6fc0e48aaecde61e35a5f4152c85f27
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412726"
---
# <a name="mfc-add-class-wizard"></a>Assistant Ajouter une classe MFC

Utilisez cet Assistant code pour ajouter une classe à un projet MFC existant, ou pour ajouter une classe à un projet ATL qui prend en charge de MFC. Vous pouvez également ajouter des classes MFC à des projets Win32 qui prend en charge MFC. Les fonctionnalités que vous avez spécifié lorsque vous avez créé votre projet déterminent les options disponibles dans cette boîte de dialogue.

## <a name="names"></a>Noms

Dans cette page, spécifiez le nom de classe, la classe de base et les noms de fichiers pour la nouvelle classe.

- **Nom de classe**

  Spécifie le nom de la nouvelle classe et fournit la base par défaut pour les noms des ID et des fichiers sur cette page. Les classes C++ commencent généralement « C », par exemple, « CMyClass » devient « Commencent », et ainsi de suite.

- **Classe de base**

  Spécifie le nom de la classe de base pour la nouvelle classe. Par défaut, la classe de base est [CWnd](../../mfc/reference/cwnd-class.md). La classe de base que vous sélectionnez détermine si les autres zones de cette page sont actifs.

  Le type de classe que vous définissez comme la classe de base détermine si la classe possède un ID de la boîte de dialogue ou un ID de ressource. Les types généraux de classes sont les suivantes :

  - Classes telles que [CButton](../../mfc/reference/cbutton-class.md), [CWnd](../../mfc/reference/cwnd-class.md), ou [CDocument](../../mfc/reference/cdocument-class.md), qui ne nécessitent pas une boîte de dialogue ID ou ID de ressource. Ces classes n’utilisent pas un ID de ressource ou la boîte de dialogue. Si vous sélectionnez un de ces classes pour votre classe de base, le **ID de la boîte de dialogue** boîte et le **ID de ressource DHTML** sont pas disponibles.

  - Classes telles que [CDialog](../../mfc/reference/cdialog-class.md), [CFormView](../../mfc/reference/cformview-class.md), ou [CPropertyPage](../../mfc/reference/cpropertypage-class.md), qui nécessitent un ID de la boîte de dialogue.

  - La classe [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md), ce qui nécessite un ID de la boîte de dialogue, un ID de ressource DHTML et un nom de fichier HTML.

  Pour les classes nécessitant un ID de la boîte de dialogue, il peut s’avérer plus efficace d’utiliser le [éditeur de ressources](../../windows/resource-editors.md) pour créer la ressource de boîte de dialogue, assigner son ID dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), puis créez une classe associée avec cet ID de ressource. Consultez [création d’une boîte de dialogue nouvelle](../../windows/creating-a-new-dialog-box.md) pour plus d’informations sur la création d’une boîte de dialogue Windows standard.

  > [!NOTE]
  > Si vous créez d’abord une ressource de boîte de dialogue et que vous dérivez sa nouvelle classe à partir de `CDHtmlDialog`, supprimer le Windows standard **OK** et **Annuler** boutons qui apparaissent dans la boîte de dialogue par défaut. La boîte de dialogue Windows standard héberge le formulaire DHTML, qui contient ses propres **OK** et **Annuler** boutons.

  Pendant que votre boîte de dialogue peut contenir des contrôles de Windows et les contrôles DHTML, il n’est pas recommandé.

- **ID de la boîte de dialogue**

  Spécifie l’ID de la boîte de dialogue, si vous avez sélectionné `CDialog`, `CFormView`, `CPropertyPage`, ou `CDHtmlDialog` en tant que le **classe de Base**.

- **Fichier .h**

  Définit le nom du fichier d’en-tête pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur celui que vous fournissez dans **Nom de classe**. Cliquez sur le bouton de sélection pour enregistrer le fichier à l’emplacement de votre choix ou pour ajouter la déclaration de classe à un fichier existant. Si vous choisissez un fichier existant, l’Assistant attend que vous cliquiez sur **Terminer** pour l’enregistrer à l’emplacement sélectionné.

  L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si la déclaration de la classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour l’ajouter au fichier ou sur **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.

- **Fichier .cpp**

  Définit le nom du fichier d’implémentation pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur celui que vous fournissez dans **Nom de classe**. Cliquez sur le bouton de sélection pour enregistrer le nom de fichier à l’emplacement de votre choix. L’Assistant attend que vous cliquiez sur **Terminer** pour enregistrer le fichier à l’emplacement sélectionné.

  L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si l’implémentation de la classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour l’ajouter au fichier ou sur **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.

- **Active accessibility**

  Permet la prise en charge de MFC pour Active Accessibility en appelant [EnableActiveAccessibility](../../mfc/reference/cwnd-class.md#enableactiveaccessibility) dans le constructeur. Cette option est disponible pour les classes dérivées à partir de [CWnd](../../mfc/reference/cwnd-class.md).

- **ID de ressource DHTML**

  S’applique aux classes dérivées de `CDHtmlDialog` uniquement. Spécifie l’ID de ressource de la boîte de dialogue DHTML. L’ID de ressource s’affiche dans la section HTML du fichier .rc du projet, ainsi que le nom de fichier de boîte de dialogue HTML. La ressource DHTML, identifiée par cet ID, qui est hébergée par la boîte de dialogue, identifié par **ID de la boîte de dialogue**.

- **. Fichier HTM**

  S’applique aux classes dérivées de `CDHtmlDialog` uniquement. Définit le nom de fichier HTML de la boîte de dialogue DHTML. Par défaut, ce nom de fichier est basé sur le nom de classe. Le nom de fichier apparaît dans la section HTML du fichier .rc du projet, ainsi que l’ID de ressource DHTML boîte de dialogue boîte.

- **Automation**

  Définit le niveau de la classe de prise en charge pour [Automation](../../mfc/automation.md). Automatisation au niveau de la classe est disponible pour toutes les classes qui prennent en charge d’Automation. Il est également disponible pour les projets créés avec la prise en charge pour l’automatisation. Autrement dit, soit un projet MFC qui [prend en charge ATL](../../atl/reference/mfc-support-in-atl-projects.md), ou un projet MFC pour lequel vous avez sélectionné le **Automation** case à cocher dans la [fonctionnalités avancées](../../mfc/reference/advanced-features-mfc-application-wizard.md) page de la bibliothèque MFC Assistant Création d’applications.

  |Option|Description|
  |------------|-----------------|
  |**Aucun**|Indique ne qu’aucune prise en charge d’Automation de la classe.|
  |**Automation**|Indique que la classe prend en charge Automation. Si vous sélectionnez cette option, la classe nouvellement créée est disponible en tant qu’objet programmable par les applications client Automation, telles que Microsoft Visual Basic et Microsoft Excel. Cette option n’est pas disponible pour les classes de base répertoriés après ce tableau.|
  |**Qui peut être créé par ID de type**|Indique que la classe et le projet prend en charge les autres applications de création d’objets de cette classe à l’aide d’Automation. Avec cette option, les clients automation peuvent créer directement un objet Automation. L’ID de type dans la zone de texte est utilisé par l’application cliente pour spécifier l’objet doit être créé ; Il est tout le système et doit être unique. Cette option n’est pas disponible pour les classes de base répertoriés après ce tableau.|

  Prise en charge Automation n’est pas disponible pour les classes de base suivantes :

  - `CAsyncMonitorFile`

  - `CAsyncSocket`

  - `CCachedDataPathProperty`

  - `CConnectionPoint`

  - `CDatabase`

  - `CDataPathProperty`

  - `CHttpFilter`

  - `CHttpServer`

  - `CInternetSession`

  - `CObject`

  - `CSocket`

- **ID du type**

  Définit l’ID de type de la classe. Le **ID de Type** zone concatène le nom du projet et le nouveau nom de classe comme suit : *MFCProj.MFCClass*. Cet ID est modifiable uniquement si vous avez sélectionné le **Automation** option **Creatable par ID de type**.

- **Générer des ressources**

  Indique que les documents créés par l’application disposent des ressources de modèle de document. Pour activer cette case à cocher, le projet doit prendre en charge l’architecture document/vue MFC et la classe de base de cette classe doit être [CFormView](../../mfc/reference/cformview-class.md).

  Consultez [modèles de Document et le processus de création de Document/vue](../../mfc/document-templates-and-the-document-view-creation-process.md) pour plus d’informations.

## <a name="see-also"></a>Voir aussi

[Classe MFC](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)
