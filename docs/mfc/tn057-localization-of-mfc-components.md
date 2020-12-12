---
description: 'En savoir plus sur : TN057 : localisation des composants MFC'
title: 'TN057 : localisation des composants MFC'
ms.date: 06/28/2018
helpviewer_keywords:
- components [MFC], localizing
- TN057
- resources [MFC], localization
- localization [MFC], MFC resources
- localization [MFC], MFC components
- MFC DLLs [MFC], localizing
- DLLs [MFC], localizing MFC
- localization [MFC], resources
ms.assetid: 5376d329-bd45-41bd-97f5-3d895a9a0af5
ms.openlocfilehash: d4a331e74acd2b5b38ae059ea180a0a2148e3a0f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214804"
---
# <a name="tn057-localization-of-mfc-components"></a>TN057 : localisation des composants MFC

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit certaines conceptions et procédures permettant de localiser votre composant, s'il s'agit d'une application ou d'une commande OLE ou d'une DLL qui utilise MFC.

## <a name="overview"></a>Vue d’ensemble

Il existe réellement deux problèmes à résoudre en localisant un composant qui utilise MFC. D'abord, vous devez localiser vos propres ressources : chaînes, boîtes de dialogue et d'autres ressources qui sont spécifiques à votre composant. La plupart des composants créés à l'aide de MFC incluent également et utilisent plusieurs ressources définies par MFC. Vous devez également fournir des ressources MFC localisées. Heureusement, plusieurs langues sont déjà fournies par l'application MFC elle-même.

De plus, votre composant doit être en mesure de s'exécuter dans son environnement cible (environnement européen ou DBCS). Dans la plupart des cas, cela dépend du mode de traitement des caractères avec le bit le plus élevé défini correctement par votre application et de la gestion des chaînes avec des caractères codés sur deux octets. Par défaut, l'application MFC est activée pour ces deux environnements, afin qu'il soit possible d'avoir un seul système binaire mondial utilisé pour toutes les plateformes avec uniquement des ressources connectées au moment de l'installation.

## <a name="localizing-your-components-resources"></a>Recherche des ressources du composant

Localiser votre application ou DLL doit impliquer simplement de remplacer les ressources par d'autres qui correspondent à la langue cible. Pour vos propres ressources, il est relativement simple de modifier les ressources dans l'éditeur de ressources et de générer votre application. Si votre code est écrit correctement, il n’y a pas de chaînes ou de texte que vous souhaitez localiser en dur dans votre code source C++. toute la localisation peut être effectuée en modifiant simplement les ressources. En fait, vous pouvez implémenter votre composant de telle sorte que ce qui est fourni par une version localisée n'implique même pas une génération du code d'origine. Cette méthode est plus complexe, mais elle en vaut la peine et correspond au mécanisme sélectionné pour l'application MFC elle-même. Il est également possible de trouver une application en chargeant le fichier EXE ou le fichier .dll dans l'éditeur de ressources et en modifiant les ressources. Si possible, cela requiert la réapplication de modifications chaque fois que vous créez une version de votre application.

Une façon d'éviter cela est de rechercher toutes les ressources dans une DLL distincte, parfois appelée DLL satellite. Cette DLL est alors chargée dynamiquement pendant l'exécution et les ressources sont chargées à partir de cette DLL au lieu du module principal avec tout votre code. MFC gère directement cette méthode. Prenez pour exemple une application appelée MYAPP.EXE ; elle peut contenir toutes ses ressources localisées dans un fichier DLL intitulé MYRES.DLL. Dans `InitInstance` de l'application, elle doit effectuer les opérations suivantes pour charger cette DLL et pour que MFC charge les ressources à partir de cet emplacement :

```cpp
CMyApp::InitInstance()
{
    // one of the first things in the init code
    HINSTANCE hInst = LoadLibrary("myres.dll");

    if (hInst != NULL)
        AfxSetResourceHandle(hInst);

    // other initialization code would follow
    // ...
}
```

À partir de là, MFC charge les ressources de cette DLL au lieu du fichier myapp.exe. Toutes les ressources, toutefois, doivent être présentes dans cette DLL ; MFC n'accèdera pas l'instance de l'application à la recherche d'une ressource donnée. Cette technique s’applique aussi bien aux DLL MFC normales qu’aux contrôles OLE. Le programme d'installation copierait la version appropriée de MYRES.DLL en fonction des paramètres régionaux de la ressource que l'utilisateur souhaiterait.

Il est relativement facile de créer une DLL de ressource uniquement. Créez un projet DLL, ajoutez-y votre fichier .RC, puis ajoutez les ressources nécessaires. Si vous avez un projet existant qui n'utilise pas cette technique, vous pouvez copier les ressources de ce projet. Après avoir ajouté le fichier de ressources au projet, vous êtes presque prêt à générer le projet. La seule chose que vous devez faire est de définir les options de l’éditeur de liens pour inclure **/noentry**. Cela indique à l’éditeur de liens que la DLL n’a pas de point d’entrée, car elle n’a pas de code, elle n’a aucun point d’entrée.

> [!NOTE]
> L'éditeur de ressources dans Visual C++ 4.0 et toute version ultérieure prend en charge plusieurs langues par fichier .RC. Cela peut faciliter la gestion de votre localisation au sein d'un projet. Les ressources de chaque langue sont contrôlées par les directives du préprocesseur générées par l'éditeur de ressources.

## <a name="using-the-provided-mfc-localized-resources"></a>Utilisation des ressources localisées fournies par MFC

Toutes les applications MFC que vous créez réutilisent deux choses de MFC : le code et les ressources. Autrement dit, MFC a plusieurs messages d'erreur, boîtes de dialogue prédéfinies et d'autres ressources utilisées par les classes MFC. Pour localiser entièrement votre application, vous devez rechercher non seulement les ressources de votre application, mais également les ressources provenant directement de MFC. MFC fournit automatiquement de nombreux fichiers de ressources de langue différentes, de sorte que si la langue que vous visez est une des langues déjà prises en charge par MFC, vous devrez simplement vérifier que vous utilisez ces ressources localisées.

Au moment de la rédaction de ce document, MFC prend en charge les langues suivantes : l'allemand, le chinois, le coréen, l'espagnol, le français, l'italien et le japonais. Les fichiers qui contiennent ces versions localisées se trouvent dans les répertoires MFC\INCLUDE\L.* ("L" signifie "localisé"). Par exemple, les fichiers allemands figurent dans le répertoire MFC\INCLUDE\L.DEU. Pour que votre application utilise ces fichiers RC au lieu des fichiers situés dans MFC\INCLUDE, ajoutez un `/IC:\PROGRAM FILES\MICROSOFT VISUAL STUDIO .NET 2003\VC7\MFC\INCLUDE\L.DEU` à votre ligne de commande RC (il ne s’agit là que d’un exemple. vous devez remplacer les paramètres régionaux de votre choix, ainsi que le répertoire dans lequel vous avez installé Visual C++).

L'instruction ci-dessus fonctionne si vos applications se lient statiquement à MFC. La plupart des applications se lient dynamiquement (parce que c'est la valeur par défaut de l'Assistant Application). Dans ce scénario, non seulement le code est lié de manière dynamique, donc les ressources. Par conséquent, vous pouvez localiser vos ressources dans votre application, mais les ressources d'implémentation MFC seront encore chargées de MFC7x.DLL (ou version ultérieure) ou de MFC7xLOC.DLL, si existant. Vous pouvez considérer ceci sous deux différents angles.

L'approche la plus complexe consiste à fournir l'un des fichiers MFC7xLOC.DLL localisés (tel que MFC7xDEU, pour l'allemand, le MFC7xESP.DLL pour l'espagnol, etc.), ou une version ultérieure, et à installer le fichier MFC7xLOC.DLL approprié dans le répertoire système lorsque l'utilisateur installe votre application. Cela peut s'avérer très complexe pour le développeur et l'utilisateur final, par conséquent cette approche n'est pas recommandée. Consultez la [note technique 56](../mfc/tn056-installation-of-localized-mfc-components.md) pour plus d’informations sur cette technique et ses inconvénients.

L'approche la plus simple et la plus sûre consiste à inclure les ressources MFC localisées dans votre application ou le fichier DLL lui-même (ou son fichier DLL satellite si vous en utilisez un). Cela évite les problèmes d'installation de MFC7xLOC.DLL. Pour ce faire, procédez de la même manière pour le cas statique fourni ci-dessus (définissant la ligne de commande RC correctement pour afficher les ressources localisées), sauf que vous devez également supprimer la définition de `/D_AFXDLL` qui a été ajoutée par AppWizard. Lorsque `/D_AFXDLL` est défini, AFXRES.H (et les autres fichiers RC MFC) ne définissent pas réellement une quelconque ressource (parce qu'elles sont extraites des DLL MFC à la place).

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
