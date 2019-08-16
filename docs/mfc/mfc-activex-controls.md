---
title: Contrôles ActiveX MFC
ms.date: 11/19/2018
f1_keywords:
- MFC ActiveX Controls (MFC)
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
ms.openlocfilehash: a1c7bb070a75f4406556817163931f0707706c40
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508123"
---
# <a name="mfc-activex-controls"></a>Contrôles ActiveX MFC

Un contrôle ActiveX est un composant logiciel réutilisable qui repose sur le modèle COM (Component Object Model), prend en charge une large gamme de fonctionnalités OLE et peut être personnalisé pour répondre à de nombreux besoins logiciels.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour un nouveau développement. Pour plus d’informations, consultez [contrôles ActiveX](activex-controls.md).

Les contrôles ActiveX sont conçus pour être utilisés dans les conteneurs de contrôles ActiveX ordinaires et sur Internet, dans World Wide Web pages. Vous pouvez créer des contrôles ActiveX avec MFC, décrit ici ou avec la [Active Template Library (ATL)](../atl/active-template-library-atl-concepts.md).

Un contrôle ActiveX peut se dessiner dans sa propre fenêtre, répondre à des événements (tels que des clics de souris) et être géré via une interface qui comprend des propriétés et des méthodes similaires à celles des objets Automation.

Ces contrôles peuvent être développés pour de nombreuses utilisations, telles que l’accès aux bases de données, la surveillance des données ou la représentation graphique. Outre leur portabilité, les contrôles ActiveX prennent en charge les fonctionnalités précédemment non disponibles pour les contrôles ActiveX, telles que la compatibilité avec les conteneurs OLE existants et la possibilité d’intégrer leurs menus avec les menus de conteneurs OLE. En outre, un contrôle ActiveX prend entièrement en charge Automation, ce qui permet au contrôle d’exposer des propriétés read\write et un ensemble de méthodes qui peuvent être appelées par l’utilisateur du contrôle.

Vous pouvez créer des contrôles ActiveX sans fenêtre et des contrôles qui créent uniquement une fenêtre lorsqu’ils deviennent actifs. Les contrôles sans fenêtre accélèrent l’affichage de votre application et permettent d’avoir des contrôles transparents et non rectangulaires. Vous pouvez également charger des propriétés de contrôle ActiveX de manière asynchrone.

Un contrôle ActiveX est implémenté en tant que serveur in-process (généralement un petit objet) qui peut être utilisé dans n’importe quel conteneur OLE. Notez que l’intégralité des fonctionnalités d’un contrôle ActiveX est disponible uniquement lorsqu’il est utilisé dans un conteneur OLE conçu pour être conscient des contrôles ActiveX. Pour obtenir la liste des conteneurs qui prennent en charge les contrôles ActiveX, consultez [contrôles ActiveX de port vers d’autres applications](../mfc/containers-for-activex-controls.md) . Ce type de conteneur, ci-après appelé «conteneur de contrôle», peut utiliser un contrôle ActiveX en utilisant les propriétés et les méthodes du contrôle, et reçoit des notifications du contrôle ActiveX sous la forme d’événements. L’illustration suivante montre cette interaction.

![Interaction entre le conteneur et le contrôle ActiveX Control](../mfc/media/vc37221.gif "Interaction entre le conteneur et le contrôle ActiveX Control") <br/>
Interaction entre un conteneur de contrôles ActiveX et un contrôle ActiveX avec fenêtres

Pour obtenir des informations récentes sur l’optimisation de vos contrôles ActiveX [, consultez contrôles ActiveX MFC: Optimisation](../mfc/mfc-activex-controls-optimization.md).

Pour créer un contrôle ActiveX MFC, consultez [créer un projet de contrôle ActiveX](../mfc/reference/mfc-activex-control-wizard.md).

Pour plus d'informations, voir :

- [Conteneurs de contrôles ActiveX](../mfc/activex-control-containers.md)

- [Documents actifs](../mfc/active-documents.md)

- [Fonctionnement des contrôles ActiveX](/windows/win32/com/activex-controls)

- [Mise à niveau d’un contrôle ActiveX existant à utiliser sur Internet](../mfc/upgrading-an-existing-activex-control.md)

##  <a name="_core_basic_components_of_an_activex_control"></a>Composants de base d’un contrôle ActiveX

Un contrôle ActiveX utilise plusieurs éléments de programmation pour interagir efficacement avec un conteneur de contrôle et avec l’utilisateur. Il s’agit de la classe [COleControl](../mfc/reference/colecontrol-class.md), d’un ensemble de fonctions de déclenchement d’événements et d’une table de dispatch.

Chaque objet de contrôle ActiveX que vous développez hérite d’un ensemble puissant de fonctionnalités de sa `COleControl`classe de base MFC,. Ces fonctionnalités incluent l’activation sur place et la logique d’automatisation. `COleControl`peut fournir l’objet de contrôle avec les mêmes fonctionnalités qu’un objet de fenêtre MFC, ainsi que la possibilité de déclencher des événements. `COleControl`peut également fournir des [contrôles sans fenêtre](../mfc/providing-windowless-activation.md), qui s’appuient sur leur conteneur pour obtenir de l’aide sur certaines des fonctionnalités fournies par une fenêtre (capture de la souris, focus clavier, défilement), mais offrent un affichage beaucoup plus rapide.

Étant donné que la classe de contrôle `COleControl`dérive de, elle hérite de la possibilité d’envoyer, ou «feu», des messages, appelés événements, au conteneur de contrôle lorsque certaines conditions sont remplies. Ces événements sont utilisés pour notifier le conteneur de contrôle quand un problème important se produit dans le contrôle. Vous pouvez envoyer des informations supplémentaires sur un événement au conteneur de contrôle en attachant des paramètres à l’événement. Pour plus d’informations sur les événements de contrôle ActiveX, [consultez l’article contrôles ActiveX MFC: Événements](../mfc/mfc-activex-controls-events.md).

Le dernier élément est un mappage de dispatch, qui est utilisé pour exposer un ensemble de fonctions (appelées méthodes) et des attributs (appelés propriétés) à l’utilisateur du contrôle. Les propriétés permettent au conteneur de contrôle ou à l’utilisateur de contrôle de manipuler le contrôle de différentes façons. L’utilisateur peut modifier l’apparence du contrôle, modifier certaines valeurs du contrôle ou effectuer des demandes du contrôle, telles que l’accès à un élément de données spécifique géré par le contrôle. Cette interface est déterminée par le développeur de contrôle et est définie à l’aide de **affichage de classes**. Pour plus d’informations sur les méthodes et les propriétés des contrôles ActiveX [, consultez l’article contrôles ActiveX MFC: Méthodes](../mfc/mfc-activex-controls-methods.md) et [Propriétés](../mfc/mfc-activex-controls-properties.md).

##  <a name="_core_interaction_between_controls_with_windows_and_activex_control_containers"></a>Interaction entre les contrôles avec des conteneurs de contrôles Windows et ActiveX

Lorsqu’un contrôle est utilisé dans un conteneur de contrôle, il utilise deux mécanismes pour communiquer: il expose des propriétés et des méthodes, et il déclenche des événements. La figure suivante illustre l’implémentation de ces deux mécanismes.

![Le contrôle ActiveX communique avec son conteneur](../mfc/media/vc37222.gif "Le contrôle ActiveX communique avec son conteneur") <br/>
Communication entre un conteneur de contrôles ActiveX et un contrôle ActiveX

La figure précédente illustre également la manière dont les autres interfaces OLE (en dehors de l’automatisation et des événements) sont gérées par les contrôles.

Toute la communication d’un contrôle avec le conteneur est effectuée par `COleControl`. Pour gérer certaines des demandes du conteneur, `COleControl` appellera les fonctions membres qui sont implémentées dans la classe de contrôle. Toutes les méthodes et certaines propriétés sont gérées de cette manière. La classe de votre contrôle peut également initier la communication avec le conteneur en appelant `COleControl`des fonctions membres de. Les événements sont déclenchés de cette manière.

##  <a name="_core_active_and_inactive_states_of_an_activex_control"></a>États actifs et inactifs d’un contrôle ActiveX

Un contrôle a deux États de base: actif et inactif. Traditionnellement, ces États étaient distingués par le fait que le contrôle avait une fenêtre. Un contrôle actif avait une fenêtre; un contrôle inactif ne l’a pas fait. Avec l’introduction de l’activation sans fenêtre, cette distinction n’est plus universelle, mais s’applique toujours à de nombreux contrôles.

Lorsqu’un [contrôle sans fenêtre](../mfc/providing-windowless-activation.md) devient actif, il appelle la capture de la souris, le focus clavier, le défilement et d’autres services de fenêtre à partir de son conteneur. Vous pouvez également [fournir une interaction souris pour les contrôles](../mfc/providing-mouse-interaction-while-inactive.md)inactifs, ainsi que créer des contrôles qui [attendent jusqu’à ce qu’ils soient activés pour créer une fenêtre](../mfc/turning-off-the-activate-when-visible-option.md).

Lorsqu’un contrôle avec une fenêtre devient actif, il peut interagir entièrement avec le conteneur de contrôle, l’utilisateur et les fenêtres. La figure ci-dessous illustre les chemins d’accès de la communication entre le contrôle ActiveX, le conteneur de contrôle et le système d’exploitation.

![Traitement des messages dans le contrôle ActiveX avec fenêtres actives](../mfc/media/vc37223.gif "Traitement des messages dans le contrôle ActiveX avec fenêtres actives") <br/>
Traitement des messages Windows dans un contrôle ActiveX avec fenêtres (lorsqu’il est actif)

##  <a name="_core_serializing_activex_elements"></a>Sérialisation

La possibilité de sérialiser des données, parfois appelée persistance, permet au contrôle d’écrire la valeur de ses propriétés dans un stockage persistant. Les contrôles peuvent ensuite être recréés en lisant l’état de l’objet à partir du stockage.

Notez qu’un contrôle n’est pas responsable de l’obtention de l’accès au support de stockage. Au lieu de cela, le conteneur du contrôle est chargé de fournir le contrôle avec un support de stockage à utiliser aux moments appropriés. Pour plus d’informations sur la sérialisation, consultez l' [article contrôles ActiveX MFC: Sérialisation en impossible.](../mfc/mfc-activex-controls-serializing.md) Pour plus d’informations sur l’optimisation de la sérialisation, consultez optimisation de la [persistance et de l’initialisation dans les](../mfc/optimizing-persistence-and-initialization.md) contrôles ActiveX: L'.

##  <a name="_core_installing_activex_control_classes_and_tools"></a>Installation des classes et des outils du contrôle ActiveX

Quand vous installez Visual C++, les classes de contrôles ActiveX MFC et les dll d’exécution de contrôle ActiveX de vente au détail et de débogage sont automatiquement installées si les contrôles ActiveX sont sélectionnés dans le programme d’installation (ils sont sélectionnés par défaut).

Par défaut, les classes et les outils de contrôle ActiveX sont installés dans les sous-répertoires suivants sous \Program Files\Microsoft Visual Studio .NET:

- **\Common7\Tools**

   Contient les fichiers de conteneur de test (TstCon32. exe, ainsi que ses fichiers d’aide).

- **\Vc7\atlmfc\include**

   Contient les fichiers include nécessaires pour développer des contrôles ActiveX avec MFC

- **\Vc7\atlmfc\src\mfc**

   Contient le code source pour des classes de contrôles ActiveX spécifiques dans MFC

- **\Vc7\atlmfc\lib**

   Contient les bibliothèques requises pour développer des contrôles ActiveX avec MFC

Il existe également des exemples pour les contrôles ActiveX MFC. Pour plus d’informations sur ces exemples, [consultez Exemples de contrôles: Contrôles ActiveX basés sur MFC](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>Voir aussi

[Éléments de l’interface utilisateur](../mfc/user-interface-elements-mfc.md)
