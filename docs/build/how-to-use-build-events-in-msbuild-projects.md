---
title: 'Procédure : Utiliser des événements de build dans des projets MSBuild'
ms.date: 11/04/2016
helpviewer_keywords:
- 'msbuild (c++), howto: use build events in projects'
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
ms.openlocfilehash: 3fe205223b6cf381bbf3e2872b1a84f9d81a3cb7
ms.sourcegitcommit: 2da5c42928739ca8cd683a9002598f28d8ec5f8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70060070"
---
# <a name="how-to-use-build-events-in-msbuild-projects"></a>Procédure : Utiliser des événements de build dans des projets MSBuild

Un événement de build est une commande que MSBuild effectue à une étape particulière du processus de génération. L’événement *pré-build* se produit avant le démarrage de la génération. l’événement avant l' *édition des liens* se produit avant le démarrage de l’étape de liaison. et l’événement après *génération* se produit une fois la génération terminée. Un événement de build se produit uniquement si l’étape de génération associée se produit. Par exemple, l’événement avant l’édition des liens ne se produit pas si l’étape de liaison n’est pas exécutée.

Chacun des trois événements de build est représenté dans un groupe de définitions d’éléments par un élément`<Command>`Command () qui est exécuté et un élément`<Message>`message () qui est affiché lorsque **MSBuild** exécute l’événement de Build. Chaque élément est facultatif et, si vous spécifiez le même élément plusieurs fois, la dernière occurrence est prioritaire.

Un élément *use-in-Build* facultatif (`<`*Build-Event*`UseInBuild>`) peut être spécifié dans un groupe de propriétés pour indiquer si l’événement de build est exécuté. La valeur du contenu d’un élément *use-in-Build* est **true** ou false. Par défaut, un événement de build est exécuté à moins que son élément *use-in-Build* correspondant `false`n’ait la valeur.

Le tableau suivant répertorie chaque élément XML d’événement de build:

|Élément XML|Description|
|-----------------|-----------------|
|`PreBuildEvent`|Cet événement s’exécute avant le début de la génération.|
|`PreLinkEvent`|Cet événement s’exécute avant le début de l’étape de liaison.|
|`PostBuildEvent`|Cet événement s’exécute une fois la génération terminée.|

Le tableau suivant répertorie chaque élément *use-in-Build* :

|Élément XML|Description|
|-----------------|-----------------|
|`PreBuildEventUseInBuild`|Spécifie s’il faut exécuter l’événement *pré-build* .|
|`PreLinkEventUseInBuild`|Spécifie s’il faut exécuter l’événement *avant l’édition des liens* .|
|`PostBuildEventUseInBuild`|Spécifie s’il faut exécuter l’événement *après génération* .|

## <a name="example"></a>Exemple

L’exemple suivant peut être ajouté à l’intérieur de l’élément Project du fichier MyProject. vcxproj créé [dans la procédure pas à pas: Utilisation de MSBuild pour créer C++ un](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)projet. Un événement *pré-build* effectue une copie de main. cpp; un événement *avant l’édition des liens* effectue une copie de main. obj; et un événement *après génération* effectue une copie de MyProject. exe. Si le projet est généré à l’aide d’une configuration Release, les événements de build sont exécutés. Si le projet est généré à l’aide d’une configuration Debug, les événements de build ne sont pas exécutés.

``` xml
<ItemDefinitionGroup>
  <PreBuildEvent>
    <Command>copy $(ProjectDir)main.cpp $(ProjectDir)copyOfMain.cpp</Command>
    <Message>Making a copy of main.cpp </Message>
  </PreBuildEvent>
  <PreLinkEvent>
    <Command>copy $(ProjectDir)$(Configuration)\main.obj $(ProjectDir)$(Configuration)\copyOfMain.obj</Command>
    <Message>Making a copy of main.obj</Message>
  </PreLinkEvent>
  <PostBuildEvent>
    <Command>copy $(ProjectDir)$(Configuration)\$(TargetFileName) $(ProjectDir)$(Configuration)\copyOfMyproject.exe</Command>
    <Message>Making a copy of myproject.exe</Message>
  </PostBuildEvent>
</ItemDefinitionGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
  <PreBuildEventUseInBuild>true</PreBuildEventUseInBuild>
  <PreLinkEventUseInBuild>true</PreLinkEventUseInBuild>
  <PostBuildEventUseInBuild>true</PostBuildEventUseInBuild>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
  <PreBuildEventUseInBuild>false</PreBuildEventUseInBuild>
  <PreLinkEventUseInBuild>false</PreLinkEventUseInBuild>
  <PostBuildEventUseInBuild>false</PostBuildEventUseInBuild>
</PropertyGroup>
```

## <a name="see-also"></a>Voir aussi

[MSBuild sur la ligne de commande - C++](msbuild-visual-cpp.md)<br/>
[Procédure pas à pas : Utilisation de MSBuild pour créer un projet C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)
