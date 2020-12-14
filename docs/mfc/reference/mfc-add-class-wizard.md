---
description: 'En savoir plus sur : Assistant Ajouter une classe MFC'
title: Assistant Ajouter une classe MFC
ms.date: 09/06/2019
f1_keywords:
- vc.codewiz.class.mfc.simple.overview
helpviewer_keywords:
- MFC Add Class Wizard
- wizards [MFC]
ms.assetid: ad3b0989-d307-43b2-9417-3f9a78889024
ms.openlocfilehash: 3f405b0f5523a183fd546790e0823e7a5e6bbbea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219250"
---
# <a name="mfc-add-class-wizard"></a>Assistant Ajouter une classe MFC

Utilisez cet Assistant Code pour ajouter une classe à un projet MFC existant, ou pour ajouter une classe à un projet ATL qui prend en charge MFC. Vous pouvez également ajouter des classes MFC aux projets Win32 qui prennent en charge MFC. Les fonctionnalités que vous avez spécifiées lors de la création de votre projet déterminent les options disponibles dans cette boîte de dialogue. Pour accéder à l’Assistant, cliquez sur **Ajouter une classe** dans l' [Assistant classe](mfc-class-wizard.md).

![Assistant Ajout d’une classe MFC](media/add-mfc-class-wizard.png "Assistant Ajout d’une classe MFC")

## <a name="names"></a>Noms

Dans cette page, spécifiez le nom de la classe, la classe de base et les noms de fichiers de la nouvelle classe.

- **Nom de la classe**

  Spécifie le nom de la nouvelle classe et fournit la base par défaut pour les noms des ID et des fichiers sur cette page. Les classes C++ commencent généralement par « C ». par exemple, « CMyClass » devient « MyClass. h », et ainsi de suite.

- **Classe de base**

  Spécifie le nom de la classe de base pour la nouvelle classe. Par défaut, la classe de base est [CWnd](../../mfc/reference/cwnd-class.md). La classe de base que vous sélectionnez détermine si les autres zones de cette page sont actives.

  Le type de classe que vous définissez comme classe de base détermine si la classe a un ID de boîte de dialogue ou un ID de ressource. Les types généraux de classes sont les suivants :

  - Les classes telles que [CButton](../../mfc/reference/cbutton-class.md), [CWnd](../../mfc/reference/cwnd-class.md)ou [CDocument](../../mfc/reference/cdocument-class.md), qui ne requièrent pas un ID de boîte de dialogue ou un ID de ressource. Ces classes n’utilisent pas d’ID de boîte de dialogue ou de ressource. Si vous sélectionnez l’une de ces classes pour votre classe de base, la zone **ID de boîte de dialogue** et la zone ID de **ressource DHTML** sont grisées.

  - Classes comme [CDialog](../../mfc/reference/cdialog-class.md), [CFormView](../../mfc/reference/cformview-class.md)ou [CPropertyPage](../../mfc/reference/cpropertypage-class.md), qui requièrent un ID de boîte de dialogue.

  - La classe [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md), qui requiert un ID de boîte de dialogue, un ID de ressource DHTML et un nom de fichier html.

  Pour les classes qui requièrent un ID de boîte de dialogue, il peut s’avérer plus efficace d’utiliser l' [éditeur de ressources](../../windows/resource-editors.md) pour créer la ressource de boîte de dialogue, d’affecter son ID dans l' [Assistant classe](mfc-class-wizard.md), puis de créer une classe associée à cet ID de ressource. Pour plus d’informations sur la création d’une boîte de dialogue Windows standard, consultez [création d’une](../../windows/creating-a-new-dialog-box.md) boîte de dialogue.

  > [!NOTE]
  > Si vous créez d’abord une ressource de boîte de dialogue et que vous dérivez sa nouvelle classe de `CDHtmlDialog` , supprimez les boutons **OK** et **Annuler** de Windows standard qui s’affichent dans la boîte de dialogue par défaut. La boîte de dialogue Windows standard héberge le formulaire DHTML, qui contient ses propres boutons **OK** et **Annuler** .

  Si votre boîte de dialogue peut contenir à la fois des contrôles Windows et des contrôles DHTML, cela n’est pas recommandé.

- **ID de boîte de dialogue**

  Spécifie l’ID de la boîte de dialogue, si vous avez sélectionné `CDialog` , `CFormView` , `CPropertyPage` ou `CDHtmlDialog` comme **classe de base**.

- **Fichier .h**

  Définit le nom du fichier d’en-tête pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur celui que vous fournissez dans **Nom de classe**. Cliquez sur le bouton de sélection pour enregistrer le fichier à l’emplacement de votre choix ou pour ajouter la déclaration de classe à un fichier existant. Si vous choisissez un fichier existant, l’Assistant attend que vous cliquiez sur **Terminer** pour l’enregistrer à l’emplacement sélectionné.

  L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si la déclaration de la classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour l’ajouter au fichier ou sur **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.

- **Fichier .cpp**

  Définit le nom du fichier d’implémentation pour la nouvelle classe d’objet. Par défaut, ce nom est basé sur celui que vous fournissez dans **Nom de classe**. Cliquez sur le bouton de sélection pour enregistrer le nom de fichier à l’emplacement de votre choix. L’Assistant attend que vous cliquiez sur **Terminer** pour enregistrer le fichier à l’emplacement sélectionné.

  L’Assistant ne remplace aucun fichier. Si vous sélectionnez le nom d’un fichier existant et que vous cliquez sur **Terminer**, l’Assistant vous invite à indiquer si l’implémentation de la classe doit être ajoutée au contenu du fichier. Cliquez sur **Oui** pour l’ajouter au fichier ou sur **Non** pour revenir à l’Assistant et spécifier un autre nom de fichier.

- **Accessibilité active**

  Active la prise en charge de MFC pour Active Accessibility en appelant [EnableActiveAccessibility](../../mfc/reference/cwnd-class.md#enableactiveaccessibility) dans le constructeur. Cette option est disponible pour les classes dérivées de [CWnd](../../mfc/reference/cwnd-class.md).

- **Automation**

  Définit le niveau de prise en charge de l' [Automation](../../mfc/automation.md)pour la classe. L’automatisation au niveau de la classe est disponible pour toutes les classes qui prennent en charge Automation. Il est également disponible pour les projets créés avec la prise en charge d’Automation. Autrement dit, soit un projet MFC qui [prend en charge ATL](../../atl/reference/mfc-support-in-atl-projects.md), soit un projet MFC pour lequel vous avez activé la case à cocher **Automation** dans la page [fonctionnalités avancées](../../mfc/reference/advanced-features-mfc-application-wizard.md) de l’Assistant Application MFC.

   La prise en charge de l’automatisation n’est pas disponible pour les classes de base suivantes :

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

## <a name="see-also"></a>Voir aussi

[Classe MFC](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)
