---
title: Contrôles ActiveX MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MFC ActiveX Controls (MFC)
dev_langs:
- C++
helpviewer_keywords:
- COleControl class [MFC], MFC ActiveX controls
- ActiveX controls [MFC], MFC
- containers [MFC], MFC ActiveX controls
- MFC ActiveX controls [MFC], serializing
- MFC ActiveX controls [MFC], containers
- serialization [MFC], MFC ActiveX controls
- dispatch maps [MFC], for MFC ActiveX controls
- MFC ActiveX controls [MFC], active/inactive state
- events [MFC], ActiveX controls
- MFC ActiveX controls [MFC]
ms.assetid: c911fb74-3afc-4bf3-a0f5-7922b14d9a1b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1209353f10e52b13202a91ae120057ba85dfa805
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930095"
---
# <a name="mfc-activex-controls"></a>Contrôles ActiveX MFC
Un contrôle ActiveX est un composant logiciel réutilisable qui repose sur le modèle COM (Component Object Model), prend en charge une large gamme de fonctionnalités OLE et peut être personnalisé pour répondre à de nombreux besoins logiciels. Contrôles ActiveX sont conçus pour une utilisation dans des conteneurs de contrôles ActiveX ordinaires et sur Internet, dans les pages du World Wide Web. Vous pouvez créer des contrôles ActiveX MFC, décrites ici, ou avec le [bibliothèque ATL (Active Template)](../atl/active-template-library-atl-concepts.md).  
  
 Un contrôle ActiveX peut se dessiner lui-même dans sa propre fenêtre, répondre aux événements (tels que des clics de souris) et être géré via une interface qui contient des propriétés et méthodes semblables à celles des objets Automation.  
  
 Ces contrôles peuvent être développés pour de nombreux usages, tels que l’accès de la base de données, les données de surveillance ou de création de graphiques. Outre leur portabilité, les contrôles ActiveX prennent en charge les fonctionnalités non disponibles précédemment pour les contrôles ActiveX, telles que la compatibilité avec des conteneurs OLE existants et la possibilité d’intégrer leurs menus avec les menus de conteneur OLE. En outre, un contrôle ActiveX prend entièrement en charge Automation, ce qui permet le contrôle exposer les propriétés en lecture-écriture et un ensemble de méthodes qui peuvent être appelées par l’utilisateur du contrôle.  
  
 Vous pouvez créer des contrôles ActiveX sans fenêtre et des contrôles qui créent une fenêtre uniquement quand ils sont activés. Les contrôles sans fenêtre accélérer l’affichage de votre application et le rendent possible d’avoir des contrôles transparents et non rectangulaires. Vous pouvez également charger les propriétés du contrôle ActiveX en mode asynchrone.  
  
 Un contrôle ActiveX est implémenté comme un serveur in-process (généralement un petit objet) qui peut être utilisé dans n’importe quel conteneur OLE. Notez que toutes les fonctionnalités d’un contrôle ActiveX sont disponible uniquement lorsque utilisé dans un conteneur OLE compatible avec des contrôles ActiveX. Consultez [contrôles ActiveX de Port pour les autres Applications](../mfc/containers-for-activex-controls.md) pour obtenir la liste des conteneurs qui prennent en charge les contrôles ActiveX. Ce type de conteneur, ci-après dénommé « conteneur de contrôle », peut exploiter un contrôle ActiveX à l’aide des propriétés et les méthodes du contrôle et reçoit des notifications à partir du contrôle ActiveX sous la forme d’événements. La figure suivante illustre cette interaction.  
  
 ![Interaction entre de conteneur de contrôles ActiveX et contrôle](../mfc/media/vc37221.gif "vc37221")  
Interaction entre un conteneur de contrôles ActiveX et un contrôle ActiveX avec fenêtres  
  
 Pour obtenir des informations récentes sur l’optimisation de vos contrôles ActiveX, consultez [contrôles ActiveX MFC : optimisation](../mfc/mfc-activex-controls-optimization.md).  
  
 Pour créer un contrôle ActiveX MFC, consultez [créer un projet de contrôle ActiveX](../mfc/reference/mfc-activex-control-wizard.md).  
  
 Pour plus d'informations, voir :  
  
-   [Conteneurs de contrôles ActiveX](../mfc/activex-control-containers.md)  
  
-   [Documents actifs](../mfc/active-documents.md)  
  
-   [Présentation des contrôles ActiveX](http://msdn.microsoft.com/library/windows/desktop/ms693753)  
  
-   [La mise à niveau d’un contrôle ActiveX à utiliser sur Internet](../mfc/upgrading-an-existing-activex-control.md)  
  
##  <a name="_core_basic_components_of_an_activex_control"></a> Composants de base d’un contrôle ActiveX  
 Un contrôle ActiveX utilise plusieurs éléments de programmation pour interagir de façon efficace avec un conteneur de contrôle et l’utilisateur. Il s’agit de classe [COleControl](../mfc/reference/colecontrol-class.md), un ensemble de fonctions de déclenchement d’événement et d’une distribution carte.  
  
 Chaque objet de contrôle ActiveX que vous développez hérite d’un ensemble de fonctions puissantes de sa classe de base MFC, `COleControl`. Ces fonctionnalités incluent l’activation sur place et la logique Automation. `COleControl` peut fournir l’objet contrôle les mêmes fonctionnalités que l’objet fenêtre MFC, plus la possibilité de déclencher des événements. `COleControl` peut également fournir [les contrôles sans fenêtre](../mfc/providing-windowless-activation.md), qui s’appuient sur leur conteneur pour les aider avec certaines des fonctionnalités une fenêtre fournit (capture de la souris, le focus clavier, le défilement), mais ils offrent affichage beaucoup plus rapide.  
  
 Étant donné que la classe du contrôle dérive `COleControl`, il hérite de la possibilité d’envoyer ou « fire », les messages, appelés événements pour le conteneur de contrôle quand certaines conditions sont remplies. Ces événements sont utilisés pour avertir le conteneur de contrôle lorsque quelque chose d’important se produit dans le contrôle. Vous pouvez envoyer des informations supplémentaires sur un événement pour le conteneur de contrôle en associant des paramètres à l’événement. Pour plus d’informations sur les événements de contrôle ActiveX, consultez l’article [contrôles ActiveX MFC : événements](../mfc/mfc-activex-controls-events.md).  
  
 Le dernier élément est une table de dispatch, qui est utilisée pour exposer un ensemble de fonctions (appelées méthodes) et d’attributs (appelés propriétés) à l’utilisateur du contrôle. Les propriétés permettent au conteneur ou l’utilisateur du contrôle pour manipuler le contrôle de différentes manières. L’utilisateur peut modifier l’apparence du contrôle, modifier certaines valeurs du contrôle ou effectuer des demandes de contrôle, comme l’accès à un élément spécifique de données qui tient à jour le contrôle. Cette interface est déterminée par le développeur de contrôle et qu’il est définie à l’aide de **affichage de classes**. Pour plus d’informations sur les propriétés et les méthodes de contrôle ActiveX, consultez les articles [contrôles ActiveX MFC : méthodes](../mfc/mfc-activex-controls-methods.md) et [propriétés](../mfc/mfc-activex-controls-properties.md).  
  
##  <a name="_core_interaction_between_controls_with_windows_and_activex_control_containers"></a> Interaction entre les contrôles avec Windows et les conteneurs de contrôles ActiveX  
 Lorsqu’un contrôle est utilisé dans un conteneur de contrôle, il utilise deux mécanismes pour communiquer : il expose les propriétés et méthodes, et il déclenche des événements. L’illustration suivante montre comment ces deux mécanismes sont implémentés.  
  
 ![Contrôle ActiveX communique avec son conteneur](../mfc/media/vc37222.gif "vc37222")  
Communication entre un conteneur de contrôles ActiveX et un contrôle ActiveX  
  
 L’illustration précédente montre également comment les autres interfaces OLE (outre l’automation et les événements) sont gérées par les contrôles.  
  
 Toutes les communications d’un contrôle avec le conteneur est effectuée par `COleControl`. Pour gérer les demandes du conteneur, `COleControl` s’appeler fonctions membres qui sont implémentées dans la classe du contrôle. Toutes les méthodes et certaines propriétés sont gérées de cette façon. Classe de votre contrôle peut également lancer la communication avec le conteneur en appelant les fonctions membres de `COleControl`. Les événements sont déclenchés de cette manière.  
  
##  <a name="_core_active_and_inactive_states_of_an_activex_control"></a> États inactif et actif d’un contrôle ActiveX  
 Un contrôle a deux états : active ou inactive. En règle générale, ces États correspondaient à la présence du contrôle ait ou non une fenêtre. Un contrôle actif avait une fenêtre ; un contrôle inactif n’ont pas. Avec l’introduction de l’activation sans fenêtre, cette distinction n’est plus universelle, mais s’applique toujours à de nombreux contrôles.  
  
 Lorsqu’un [contrôle sans fenêtre](../mfc/providing-windowless-activation.md) est actif, il appelle la capture de la souris, le focus clavier, le défilement et autres services de fenêtre à partir de son conteneur. Vous pouvez également [fournir une interaction souris aux contrôles inactifs](../mfc/providing-mouse-interaction-while-inactive.md), ainsi que de créer des contrôles [attendre activé pour créer une fenêtre](../mfc/turning-off-the-activate-when-visible-option.md).  
  
 Lorsqu’un contrôle avec une fenêtre devienne actif, elle est capable d’interagir entièrement avec le conteneur de contrôle, l’utilisateur et Windows. La figure ci-dessous montre les chemins d’accès de la communication entre le contrôle ActiveX, le conteneur de contrôle et le système d’exploitation.  
  
 ![Dans le contrôle ActiveX avec fenêtres actif le traitement des messages](../mfc/media/vc37223.gif "vc37223")  
Windows traitement des messages dans un contrôle ActiveX avec fenêtres (lorsqu’il est actif)  
  
##  <a name="_core_serializing_activex_elements"></a> sérialisation  
 La capacité à sérialiser des données, parfois appelée persistance, permet au contrôle d’écrire la valeur de ses propriétés dans un stockage persistant. Contrôles peuvent ensuite être recréés en lisant l’état de l’objet à partir du stockage.  
  
 Notez qu’un contrôle n’est pas responsable de l’obtention de l’accès au support de stockage. Au lieu de cela, le conteneur du contrôle est chargé de fournir le contrôle avec un support de stockage à utiliser au moment voulu. Pour plus d’informations sur la sérialisation, consultez l’article [contrôles ActiveX MFC : sérialisation](../mfc/mfc-activex-controls-serializing.md). Pour plus d’informations sur l’optimisation de la sérialisation, consultez [optimisation de la persistance et l’initialisation](../mfc/optimizing-persistence-and-initialization.md) dans les contrôles ActiveX : optimisation.  
  
##  <a name="_core_installing_activex_control_classes_and_tools"></a> L’installation des outils et des Classes de contrôles ActiveX  
 Lorsque vous installez Visual C++, MFC ActiveX contrôler des classes et la vente au détail et déboguer le contrôle ActiveX DLL d’exécution sont installés automatiquement si les contrôles ActiveX sont sélectionnés dans le programme d’installation (ils sont sélectionnés par défaut).  
  
 Par défaut, les classes de contrôles ActiveX et les outils sont installés dans les sous-répertoires \Program Files\Microsoft Visual Studio .NET suivants :  
  
-   **\Common7\Tools**  
  
     Contient les fichiers du conteneur de Test (TstCon32.exe, ainsi que ses fichiers d’aide).  
  
-   **\Vc7\atlmfc\include**  
  
     Contient les fichiers include requis pour développer des contrôles ActiveX MFC  
  
-   **\Vc7\atlmfc\src\mfc**  
  
     Contient le code source pour les classes de contrôles ActiveX spécifiques dans MFC  
  
-   **\Vc7\atlmfc\lib**  
  
     Contient les bibliothèques nécessaires pour développer des contrôles ActiveX MFC  
  
 Il existe également des exemples de contrôles ActiveX MFC. Pour plus d’informations sur ces exemples, consultez [exemples de contrôles : contrôles ActiveX MFC](../visual-cpp-samples.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments d’Interface utilisateur](../mfc/user-interface-elements-mfc.md)
