---
title: "Portage vers la plateforme Windows universelle (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: f662d2e4-8940-418d-8109-cb76cb8f8569
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Portage vers la plateforme Windows universelle (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Dans cette rubrique, vous trouverez des informations sur la façon de porter du code C\+\+ existant vers la plateforme d’application Windows 10, la plateforme Windows universelle. Le terme *universel* signifie que votre code peut s'exécuter sur tout appareil équipé de Windows 10, notamment les ordinateurs de bureau, les téléphones, les tablettes et les appareils nouvelle génération qui exécutent Windows 10. Avec Windows 8.1, vous deviez créer une application ciblant à la fois Windows 8.1 et Windows Phone 8.1 à l'aide d'une fonctionnalité système de projet spécial appelée projet partagé. Les applications Windows universelles ne font pas appel à ce mécanisme. Au lieu de cela, vous utilisez un projet unique et un code XAML unique qui fonctionne correctement sur n'importe quel appareil exécutant Windows 10. Vous pouvez utiliser les fonctionnalités de disposition dynamique de XAML pour permettre à l'interface utilisateur de l'application de s'adapter à différentes tailles d'affichage.  
  
 La documentation du Centre de développement Windows contient un guide de portage d’applications Windows 8.1 vers la plateforme Windows universelle. Consultez [Passer de Windows Runtime 8 à la plateforme Windows universelle](http://msdn.microsoft.com/library/windows/apps/dn954974.aspx). Bien que le guide soit axé essentiellement sur le code C\#, la plupart des conseils sont applicables à C\+\+. Les procédures suivantes contiennent des informations plus détaillées.  
  
 Cette rubrique contient les procédures suivantes relatives au portage de code vers la plateforme Windows universelle \(UWP\).  
  
1.  [Portage d’une application du Windows Store Windows 8.1 vers UWP](#BK_81StoreApp)  
  
2.  [Portage d'un composant d'exécution Windows 8.1 vers UWP](#BK_81Component)  
  
 Si vous avez une DLL Win32 de bureau classique et que vous souhaitez l’appeler à partir d’une application UWP, c’est également possible. Ces procédures vous permettent de créer une couche d’interface utilisateur UWP pour une application C\+\+ de bureau Windows classique existante ou votre code C\+\+ standard multiplateforme. Consultez [Comment : utiliser le code C\+\+ existant dans une application pour la plateforme Windows universelle](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md).  
  
##  <a name="BK_81StoreApp"></a> Portage d’une application du Windows Store Windows 8.1 vers UWP  
 Si vous avez une application du Windows Store Windows 8.1, vous pouvez appliquer cette procédure pour qu'elle fonctionne sur la plateforme UWP et sur tout appareil qui exécute Windows 10.  Il est préférable de créer d'abord le projet avec [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] comme projet Windows 8.1, pour éliminer les problèmes résultant des modifications apportées au compilateur et aux bibliothèques. Une fois cette opération terminée, il existe deux façons de convertir un projet UWP Windows 10. Le moyen le plus simple \(comme expliqué dans la procédure suivante\) consiste à créer un projet Windows universel et à y copier votre code existant. Si vous utilisiez un projet universel pour la version de bureau de Windows 8.1 et pour Windows Phone 8.1, votre projet commencera avec deux dispositions différentes en XAML, mais finira avec une disposition dynamique unique qui s'adapte à la taille d'affichage. La deuxième façon de convertir un projet Windows 10 consiste à modifier le fichier projet et le fichier Package.appxmanifest. Cette méthode est expliquée dans [Migrer des applications vers la plateforme Windows universelle](../misc/migrate-apps-to-the-universal-windows-platform-uwp.md).  
  
#### Pour porter une application du Windows Store Windows 8.1 vers UWP  
  
1.  Si ce n'est déjà fait, ouvrez votre projet d'application Windows 8.1 dans [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] et suivez les instructions pour mettre à niveau le fichier projet.  
  
     Vous devez avoir installé les Outils Windows 8.1 dans le programme d'installation de Visual Studio. Si ces outils ne sont pas installés, démarrez le programme d'installation de Visual Studio à partir de la fenêtre Programmes et fonctionnalités, choisissez [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] puis, dans la fenêtre d'installation, choisissez **Modifier**. Recherchez Outils Windows 8.1, assurez\-vous que cette option est sélectionnée et cliquez sur OK.  
  
2.  Ouvrez la fenêtre Propriétés du projet et, sous C\+\+, Général, définissez v140 \(les outils de génération pour [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)]\) comme ensemble d'outils de plateforme.  
  
3.  Générez le projet comme projet Windows 8.1 et résolvez les éventuelles erreurs de génération. À ce stade, les erreurs sont probablement dues à des modifications avec rupture dans les outils de génération et les bibliothèques. Consultez [Modifications avec rupture dans Visual C\+\+ 2015](../porting/visual-cpp-change-history-2003-20151.md) pour une explication détaillée des modifications qui peuvent affecter votre code.  
  
     Une fois votre projet généré correctement, vous êtes prêt à effectuer le portage vers UWP \(Windows 10\).  
  
4.  Créez un projet d'application Windows universelle à l'aide du modèle Vierge. Vous souhaiterez peut\-être lui donner le même nom que votre projet existant, bien que pour cela les projets doivent être dans des répertoires différents.  
  
5.  Fermez la solution puis, à l'aide de l'Explorateur Windows ou de la ligne de commande, copiez les fichiers de code \(avec les extensions .cpp, .h et .xaml\) de votre projet Windows 8.1 vers le même dossier que le fichier projet \(.vcxproj\) pour le projet que vous avez créé à l'étape 1. Ne copiez pas le fichier Package.appxmanifest et, si vous avez du code distinct pour la version de bureau de Windows 8.1 et pour Windows Phone, choisissez l'une des deux versions à porter en premier \(vous devrez effectuer certaines tâches ultérieurement pour adapter l'autre version\). Veillez à copier les sous\-dossiers et leur contenu. Si vous y êtes invité, choisissez de remplacer les fichiers ayant des noms dupliqués.  
  
6.  Rouvrez la solution et choisissez **Ajouter, Élément existant** dans le menu contextuel du nœud du projet. Sélectionnez tous les fichiers que vous avez copiés, à l'exception de ceux qui font déjà partie du projet.  
  
     Vérifiez tous les sous\-dossiers et veillez à y ajouter également les fichiers.  
  
7.  Si vous n'utilisez pas le même nom que celui de votre ancien projet, ouvrez le fichier Package.appxmanifest et mettez à jour le point d'entrée pour refléter le nom de l'espace de noms pour la classe App.  
  
     Le champ **Point d'entrée** dans le fichier Package.appxmanifest contient un nom inclus dans l'étendue pour la classe App, qui comprend l'espace de noms contenant la classe App. Quand vous créez un projet d'application Windows universelle, l'espace de noms est défini sur le nom du projet. S'il diffère de ce qui figure dans les fichiers que vous avez copiés depuis votre ancien projet, vous devez mettre l'un ou l'autre à jour pour qu'ils correspondent.  
  
8.  Générez le projet et résolvez les éventuelles erreurs de génération dues à des changements entre les différentes versions du Kit de développement logiciel Windows.  
  
9. Exécutez le projet sur le bureau local. Vérifiez qu'il n'y a aucune erreur de déploiement, que la disposition de l'application semble correcte et qu'elle fonctionne correctement sur le bureau.  
  
10. Si vous aviez des fichiers de code et .xaml distincts pour un autre appareil, tel que Windows Phone 8.1, examinez ce code et identifiez où il diffère de l'appareil standard. Si la différence ne concerne que la disposition, vous pourrez peut\-être utiliser un gestionnaire d’état visuel dans le code xaml pour personnaliser l’affichage en fonction de la taille de l’écran. Pour les autres différences, vous pouvez utiliser des sections de conditions dans votre code en utilisant les instructions \#if suivantes.  
  
    ```  
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP) #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP) #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP) #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)  
    ```  
  
     Ces instructions s’appliquent respectivement aux applications du Windows Store, aux applications du Windows Phone Store, aux deux ou bien aux applications de bureau Win32 classiques uniquement. Ces macros sont uniquement disponibles dans le Kit de développement logiciel \(SDK\) Windows 8.1 et versions ultérieures. Par conséquent, si votre code doit être compilé avec des versions antérieures du SDK Windows ou pour d’autres plateformes non\-Windows, vous devez également vous préparer à l’éventualité qu’aucune de ces macros ne soit définie.  
  
11. Exécutez et déboguez l’application sur un émulateur ou un appareil physique pour chaque type d’appareil pris en charge par votre application. Pour exécuter un émulateur, vous devez exécuter Visual Studio sur un ordinateur physique, et non sur un ordinateur virtuel.  
  
##  <a name="BK_81Component"></a> Portage d'un composant d'exécution Windows 8.1 vers UWP  
 Si vous avez une DLL ou un composant Windows Runtime qui fonctionne déjà avec les applications du Windows Store Windows 8.1, vous pouvez appliquer cette procédure pour faire en sorte que le composant ou la DLL fonctionne avec la plateforme UWP et Windows 10. La procédure de base consiste à créer un projet et à y copier votre code.  
  
#### Pour porter un composant d'exécution Windows 8.1 vers UWP  
  
1.  Dans la boîte de dialogue **Nouveau projet** dans [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)], localisez le nœud **Windows universel**. Si vous ne voyez pas ce nœud, installez d’abord les [Outils pour Windows 10](http://go.microsoft.com/fwlink/p/?LinkID=617903). Choisissez le modèle **Composant Windows Runtime**, donnez un nom à votre composant, puis choisissez le bouton **OK**. Le nom du composant sera utilisé comme nom de l’espace de noms. C’est pourquoi il est conseillé d’utiliser le même nom que celui de l’espace de noms de vos anciens projets. Pour ce faire, vous devez créer le projet dans un dossier autre que celui de l'ancien. Si vous choisissez un nom différent, vous pouvez mettre à jour le nom de l'espace de noms dans les fichiers de code générés.  
  
2.  Fermez le projet.  
  
3.  Copiez tous les fichiers de code \(.cpp, .h, .xaml, etc.\) depuis votre composant Windows 8.1 dans votre projet nouvellement créé. Ne copiez pas le fichier Package.appxmanifest.  
  
4.  Générez le projet et résolvez toutes les erreurs dues à des modifications avec rupture entre les différentes versions du Kit de développement logiciel Windows \(Kit SDK Windows\).  
  
## Résolution des problèmes  
 Différentes erreurs peuvent survenir lors du processus de portage de code vers la plateforme Windows universelle. Voici quelques\-uns des problèmes que vous pouvez rencontrer.  
  
 **Problèmes de configuration de projet**  
  
 L’erreur suivante peut s’afficher :  
  
```Output  
impossible de trouver l’assembly ’platform.winmd’ : spécifiez le chemin de recherche des assemblys en utilisant /AI ou en définissant la variable d’environnement LIBPATH  
```  
  
 Dans ce cas, le projet n’est pas créé en tant que projet d’application Windows universelle. Vérifiez le fichier projet et assurez\-vous qu’il comporte les éléments XML corrects qui identifient un projet comme projet d’application Windows universelle. Les éléments suivants doivent être présents \(le numéro de version de la plateforme cible peut être différent\) :  
  
```xml  
<AppContainerApplication>true</AppContainerApplication> <ApplicationType>Windows Store</ApplicationType> <WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion> <WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion> <ApplicationTypeRevision>10.0</ApplicationTypeRevision>  
```  
  
 Si vous avez créé un nouveau projet pour la plateforme Windows universelle à l’aide de Visual Studio, cette erreur ne doit normalement pas s’afficher.  
  
## Voir aussi  
 [Visual C\+\+ Porting Guide](../porting/porting-to-the-universal-windows-platform-cpp.md)   
 [Développer des applications pour la plateforme Windows universelle \(UWP\)](../Topic/Develop%20apps%20for%20the%20Universal%20Windows%20Platform%20\(UWP\).md)