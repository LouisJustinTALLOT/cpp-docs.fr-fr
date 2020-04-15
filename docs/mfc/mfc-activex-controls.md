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
ms.openlocfilehash: e9cc38eebed0b1f8e0932e89ef1452261aefd7dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365439"
---
# <a name="mfc-activex-controls"></a>Contrôles ActiveX MFC

Un contrôle ActiveX est un composant logiciel réutilisable qui repose sur le modèle COM (Component Object Model), prend en charge une large gamme de fonctionnalités OLE et peut être personnalisé pour répondre à de nombreux besoins logiciels.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne devrait pas être utilisée pour de nouveaux développements. Pour plus d’informations, voir [ActiveX Controls](activex-controls.md).

Les contrôles ActiveX sont conçus pour être utilisés à la fois dans les conteneurs de contrôle ActiveX ordinaires et sur Internet, dans les pages Web du monde entier. Vous pouvez créer des contrôles ActiveX soit avec MFC, décrit ici, ou avec la [Bibliothèque Active Template (ATL)](../atl/active-template-library-atl-concepts.md).

Un contrôle ActiveX peut se dessiner dans sa propre fenêtre, répondre à des événements (tels que les clics de souris), et être géré à travers une interface qui comprend des propriétés et des méthodes similaires à celles des objets Automation.

Ces contrôles peuvent être développés pour de nombreuses utilisations, telles que l’accès aux bases de données, la surveillance des données ou le graphique. Outre leur portabilité, ActiveX contrôle les fonctionnalités de support précédemment non disponibles pour les contrôles ActiveX, telles que la compatibilité avec les conteneurs OLE existants et la possibilité d’intégrer leurs menus avec les menus des conteneurs OLE. En outre, un contrôle ActiveX prend pleinement en charge Automation, ce qui permet au contrôle d’exposer les propriétés de lecture et un ensemble de méthodes qui peuvent être appelées par l’utilisateur de contrôle.

Vous pouvez créer des commandes et des contrôles ActiveX sans fenêtre qui ne créent une fenêtre que lorsqu’elles deviennent actives. Les commandes sans fenêtre accélèrent l’affichage de votre application et permettent d’avoir des commandes transparentes et non-spécululaires. Vous pouvez également charger les propriétés de contrôle ActiveX de manière asynchrone.

Un contrôle ActiveX est implémenté comme un serveur en cours (généralement un petit objet) qui peut être utilisé dans n’importe quel conteneur OLE. Notez que la fonctionnalité complète d’un contrôle ActiveX n’est disponible que lorsqu’elle est utilisée dans un conteneur OLE conçu pour être au courant des commandes ActiveX. Consultez [Port ActiveX Controls to Other Applications](../mfc/containers-for-activex-controls.md) pour une liste de conteneurs qui prennent en charge les contrôles ActiveX. Ce type de conteneur, appelé ci-après un « conteneur de contrôle », peut utiliser un contrôle ActiveX en utilisant les propriétés et les méthodes du contrôle, et reçoit des notifications du contrôle ActiveX sous forme d’événements. Le chiffre suivant démontre cette interaction.

![Interaction du conteneur ActiveX et du contrôle](../mfc/media/vc37221.gif "Interaction du conteneur ActiveX et du contrôle") <br/>
Interaction entre un conteneur de contrôle ActiveX et un contrôle ActiveX windows

Pour des informations récentes sur l’optimisation de vos contrôles ActiveX, voir [MFC ActiveX Controls: Optimization](../mfc/mfc-activex-controls-optimization.md).

Pour créer un contrôle MFC ActiveX, voir [Créer un projet de contrôle ActiveX](../mfc/reference/mfc-activex-control-wizard.md).

Pour plus d'informations, consultez les pages suivantes :

- [Conteneurs de contrôle ActiveX](../mfc/activex-control-containers.md)

- [Documents actifs](../mfc/active-documents.md)

- [Comprendre les contrôles ActiveX](/windows/win32/com/activex-controls)

- [Mise à niveau d’un contrôle ActiveX existant à utiliser sur Internet](../mfc/upgrading-an-existing-activex-control.md)

## <a name="basic-components-of-an-activex-control"></a><a name="_core_basic_components_of_an_activex_control"></a>Composants de base d’un contrôle ActiveX

Un contrôle ActiveX utilise plusieurs éléments programmatiques pour interagir efficacement avec un conteneur de contrôle et avec l’utilisateur. Il s’agit de la classe [COleControl](../mfc/reference/colecontrol-class.md), un ensemble de fonctions de tir événementiel, et une carte de répartition.

Chaque objet de contrôle ActiveX que vous développez hérite `COleControl`d’un puissant ensemble de fonctionnalités de sa classe de base MFC, . Ces caractéristiques incluent l’activation sur place, et la logique d’automatisation. `COleControl`peut fournir à l’objet de contrôle la même fonctionnalité qu’un objet de fenêtre MFC, ainsi que la possibilité de tirer des événements. `COleControl`peut également fournir des [contrôles sans fenêtre](../mfc/providing-windowless-activation.md), qui comptent sur leur conteneur pour obtenir de l’aide avec certaines des fonctionnalités d’une fenêtre fournit (capture de souris, mise au point du clavier, défilement), mais offrent un affichage beaucoup plus rapide.

Parce que la classe `COleControl`de contrôle dérive de , il hérite de la capacité d’envoyer, ou «feu», des messages, appelés événements, au conteneur de contrôle lorsque certaines conditions sont remplies. Ces événements sont utilisés pour aviser le conteneur de contrôle lorsque quelque chose d’important se produit dans le contrôle. Vous pouvez envoyer des informations supplémentaires sur un événement au conteneur de contrôle en attachant des paramètres à l’événement. Pour plus d’informations sur les événements de contrôle ActiveX, voir l’article [MFC ActiveX Controls: Events](../mfc/mfc-activex-controls-events.md).

L’élément final est une carte de répartition, qui est utilisée pour exposer un ensemble de fonctions (appelées méthodes) et attributs (appelés propriétés) à l’utilisateur de contrôle. Les propriétés permettent au conteneur de contrôle ou à l’utilisateur de contrôle de manipuler le contrôle de diverses façons. L’utilisateur peut modifier l’apparence du contrôle, modifier certaines valeurs du contrôle ou faire des demandes de contrôle, comme l’accès à un élément spécifique de données que le contrôle maintient. Cette interface est déterminée par le développeur de contrôle et est définie à l’aide **de Class View**. Pour plus d’informations sur les méthodes et les propriétés de contrôle ActiveX, voir les articles [MFC ActiveX Controls: Methods](../mfc/mfc-activex-controls-methods.md) and [Properties](../mfc/mfc-activex-controls-properties.md).

## <a name="interaction-between-controls-with-windows-and-activex-control-containers"></a><a name="_core_interaction_between_controls_with_windows_and_activex_control_containers"></a>Interaction entre les contrôles avec Windows et les conteneurs de contrôle ActiveX

Lorsqu’un contrôle est utilisé dans un conteneur de contrôle, il utilise deux mécanismes pour communiquer : il expose les propriétés et les méthodes, et il déclenche des événements. Le chiffre suivant montre comment ces deux mécanismes sont mis en œuvre.

![Le contrôle ActiveX communique avec son conteneur](../mfc/media/vc37222.gif "Le contrôle ActiveX communique avec son conteneur") <br/>
Communication entre un conteneur de contrôle ActiveX et un contrôle ActiveX

Le chiffre précédent illustre également comment d’autres interfaces OLE (en plus de l’automatisation et des événements) sont traitées par des contrôles.

Toute la communication d’un contrôle avec `COleControl`le conteneur est effectuée par . Pour répondre à certaines des `COleControl` demandes du conteneur, appelez les fonctions des membres qui sont mises en œuvre dans la classe de contrôle. Toutes les méthodes et certaines propriétés sont traitées de cette façon. La classe de votre contrôle peut également initier la `COleControl`communication avec le conteneur en appelant les fonctions des membres de . Les événements sont déclenchés de cette manière.

## <a name="active-and-inactive-states-of-an-activex-control"></a><a name="_core_active_and_inactive_states_of_an_activex_control"></a>États actifs et inactifs d’un contrôle ActiveX

Un contrôle a deux états de base: actif et inactif. Traditionnellement, ces États se distinguaient par la question de savoir si le contrôle avait une fenêtre. Un contrôle actif avait une fenêtre; un contrôle inactif ne l’a pas fait. Avec l’introduction d’une activation sans fenêtre, cette distinction n’est plus universelle, mais s’applique toujours à de nombreux contrôles.

Lorsqu’un [contrôle sans fenêtre](../mfc/providing-windowless-activation.md) devient actif, il invoque la capture de la souris, la mise au point du clavier, le défilement et d’autres services de fenêtre à partir de son conteneur. Vous pouvez également [fournir l’interaction de souris aux contrôles inactifs,](../mfc/providing-mouse-interaction-while-inactive.md)ainsi que créer des contrôles qui [attendent jusqu’à activé pour créer une fenêtre.](../mfc/turning-off-the-activate-when-visible-option.md)

Lorsqu’un contrôle avec une fenêtre devient actif, il est capable d’interagir pleinement avec le conteneur de contrôle, l’utilisateur et Windows. La figure ci-dessous montre les voies de communication entre le contrôle ActiveX, le conteneur de contrôle et le système d’exploitation.

![Contrôle ActiveX avec fenêtres actives pour le traitement des messages](../mfc/media/vc37223.gif "Contrôle ActiveX avec fenêtres actives pour le traitement des messages") <br/>
Traitement des messages Windows dans un contrôle ActiveX windows (Lorsqu’il est actif)

## <a name="serialization"></a><a name="_core_serializing_activex_elements"></a>Sérialisation

La capacité de sérialiser des données, parfois appelée persistance, permet au contrôle d’écrire la valeur de ses propriétés au stockage persistant. Les commandes peuvent ensuite être recréées en lisant l’état de l’objet à partir du stockage.

Notez qu’un contrôle n’est pas responsable de l’accès au support de stockage. Au lieu de cela, le conteneur du contrôleur est responsable de fournir au contrôle un moyen de stockage à utiliser aux moments appropriés. Pour plus d’informations sur la sérialisation, voir l’article [MFC ActiveX Controls: Serializing](../mfc/mfc-activex-controls-serializing.md). Pour plus d’informations sur l’optimisation de la sérialisation, voir [Optimiser la persistance et l’initialisation](../mfc/optimizing-persistence-and-initialization.md) dans ActiveX Controls: Optimization.

## <a name="installing-activex-control-classes-and-tools"></a><a name="_core_installing_activex_control_classes_and_tools"></a>Installation de classes et d’outils de contrôle ActiveX

Lorsque vous installez Visual CMD, les classes de contrôle MFC ActiveX et les DLS de commande ActiveX de détail et de débogé sont automatiquement installés si les commandes ActiveX sont sélectionnées dans Setup (elles sont sélectionnées par défaut).

Par défaut, les classes de contrôle ActiveX et les outils sont installés dans les sous-directions suivants sous le site de 'Program Files’Microsoft Visual Studio .NET:

- **Outils communs**

   Contient les fichiers De conteneurs de test (TstCon32.exe, ainsi que ses fichiers d’aide).

- **'Vc7'atlmfc' comprennent**

   Contient les fichiers inclus nécessaires pour développer des contrôles ActiveX avec MFC

- **'Vc7'atlmfc’src’mfc**

   Contient le code source pour des classes de contrôle ActiveX spécifiques dans MFC

- **Vc7 atlmfc-lib**

   Contient les bibliothèques nécessaires pour développer des contrôles ActiveX avec MFC

Il existe également des échantillons pour les commandes MFC ActiveX. Pour plus d’informations sur ces échantillons, voir [Contrôles Échantillons: MFC-Based ActiveX Controls](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>Voir aussi

[Éléments d’interface utilisateur](../mfc/user-interface-elements-mfc.md)
