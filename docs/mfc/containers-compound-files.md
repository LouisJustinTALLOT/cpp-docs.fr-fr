---
title: 'Conteneurs : Fichiers composés | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- compound files [MFC]
- compound documents
- containers [MFC], compound files
- OLE documents [MFC], compound files
- performance [MFC], compound files
- files [MFC], compound
- standardized file structure compound files
- documents [MFC], compound
- documents [MFC], OLE
- OLE containers [MFC], compound files
- access modes for files [MFC]
ms.assetid: 8b83cb3e-76c8-4bbe-ba16-737092b36f49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a8bee847d1121a6d5da1679c29a9107c8a447ab1
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930223"
---
# <a name="containers-compound-files"></a>Conteneurs : fichiers composés
Cet article décrit les composants et l'implémentation des fichiers composés, ainsi que les avantages et les inconvénients liés à l'utilisation de fichiers composés dans vos applications OLE.  
  
 Les fichiers font partie intégrante d'OLE. Ils permettent de simplifier le transfert de données et le stockage de documents OLE. Les fichiers composés sont une implémentation du modèle de stockage structuré actif. Il existe des interfaces cohérentes qui prennent en charge cette sérialisation sur un stockage, un flux de données ou un fichier objet. Les fichiers composés sont pris en charge dans la bibliothèque MFC par les classes `COleStreamFile` et `COleDocument`.  
  
> [!NOTE]
>  L'utilisation d'un fichier composé n'implique pas que les informations proviennent d'un document OLE ou d'un document composé. Les fichiers composés sont juste l'un des moyens de stocker des documents composés, des documents OLE et d'autres données.  
  
##  <a name="_core_components_of_a_compound_file"></a> Composants d’un fichier composé  
 L'implémentation OLE des fichiers composés utilise trois types d'objets : objets de flux, objets de stockage et objets `ILockBytes`. Ces objets sont semblables aux composants d'un système de fichiers standard selon les manières suivantes :  
  
-   Les objets de flux, tels que les fichiers, stockent des données de n'importe quel type.  
  
-   Les objets de stockage, comme les répertoires, peuvent contenir d'autres objets de stockage et de flux.  
  
-   `LockBytes` les objets représentent l’interface entre les objets de stockage et le matériel physique. Elles déterminent la manière dont les octets réels sont écrites sur le périphérique de stockage du `LockBytes` objet accède, comme un disque dur ou d’une zone de mémoire globale. Pour plus d’informations sur `LockBytes` objets et la `ILockBytes` l’interface, consultez la *référence du programmeur OLE*.  
  
##  <a name="_core_advantages_and_disadvantages_of_compound_files"></a> Avantages et inconvénients des fichiers composés  
 Les fichiers composés offrent des avantages non disponibles avec les méthodes précédentes de stockage de fichiers. Elles comprennent :  
  
-   Accès incrémentiel aux fichiers.  
  
-   Modes d'accès aux fichiers.  
  
-   Standardisation de la structure des fichiers.  
  
 Les inconvénients potentiels des fichiers composés (taille importante et problèmes de performances liées au stockage sur les disquettes) doivent être pris en compte lorsque vous décidez si vous allez les utiliser ou non dans votre application.  
  
###  <a name="_core_incremental_access_to_files"></a> Accès incrémentiel aux fichiers  
 L'accès incrémentiel aux fichiers est un avantage automatique de l'utilisation des fichiers composés. Étant donné qu'un fichier composé peut être affiché sous la forme d'un "système de fichiers dans un fichier", chaque type d'objet, tel que le flux ou le stockage de données, est accessible sans avoir besoin de charger le fichier complet. Cela peut réduire considérablement le temps d'accès d'une application à de nouveaux objets que l'utilisateur souhaiterait modifier. La mise à jour incrémentielle, selon le même concept, présente des avantages similaires. Au lieu d'enregistrer tout le fichier dans le but d'enregistrer uniquement les modifications apportées à un objet, OLE stocke simplement l'objet de flux ou de stockage modifié par l'utilisateur.  
  
###  <a name="_core_file_access_modes"></a> Modes d’accès au fichier  
 Pouvoir déterminer quand les modifications apportées aux objets d’un fichier composé sont validées sur le disque est un autre avantage des fichiers composés. Le mode selon lequel les fichiers sont accessibles, soit de manière directe soit après traitement, détermine le moment où les modifications sont validées.  
  
-   Le mode de traitement utilise une opération de validation en deux phases pour modifier les objets dans un fichier composé, en gardant ainsi disponibles les copies anciennes et nouvelles du document jusqu'à ce que l'utilisateur choisisse soit d'enregistrer soit d'annuler les modifications.  
  
-   Le mode direct intègre les modifications apportées au document à mesure qu'elles sont effectuées, sans possibilité de les annuler ultérieurement.  
  
 Pour plus d’informations sur les modes d’accès, consultez la *référence du programmeur OLE*.  
  
###  <a name="_core_standardization"></a> Normalisation  
 La structure standardisée des fichiers composés permet aux applications OLE de parcourir les fichiers composés créés par votre application OLE sans savoir quelle application a réellement créé le fichier.  
  
###  <a name="_core_size_and_performance_considerations"></a> Taille et améliorer les performances  
 Du fait de la complexité de la structure de stockage des fichiers composés et de la possibilité d'enregistrer des données de façon incrémentielle, les fichiers utilisant ce format sont susceptibles d'être plus grands que les autres fichiers utilisant le stockage non structuré ou "fichier plat". Si votre application charge et enregistre souvent des fichiers, le recours aux fichiers composés peut entraîner l'augmentation de la taille des fichiers beaucoup plus rapidement que les fichiers non composés. Puisque les fichiers composés peuvent être volumineux, le temps d'accès des fichiers stockés et chargés à partir des disquettes peut également être affecté, ce qui donne un accès plus lent aux fichiers.  
  
 L'autre problème qui affecte les performances est la fragmentation des fichiers composés. La taille d'un fichier composé est déterminée par la différence entre le premier et le dernier secteur de disque utilisés par le fichier. Un fichier fragmenté peut contenir plusieurs zones d'espace libre qui ne contiennent pas de données, mais qui sont comptées lors du calcul de la taille. Pendant la durée de vie d'un fichier composé, ces zones sont créées par l'insertion ou la suppression d'objets de stockage.  
  
##  <a name="_core_using_compound_files_format_for_your_data"></a> À l’aide du Format des fichiers composés pour vos données  
 Après avoir créé avec succès une application qui possède une classe de document dérivée de `COleDocument`, assurez-vous que le constructeur de votre document principal appelle `EnableCompoundFile`. Lorsque l'Assistant d'application crée des applications de conteneur OLE, cet appel est inséré automatiquement.  
  
 Dans le *référence du programmeur OLE*, consultez [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034), [IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015), et [ILockBytes](http://msdn.microsoft.com/library/windows/desktop/aa379238).  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneurs](../mfc/containers.md)   
 [Conteneurs : Problèmes d’Interface utilisateur](../mfc/containers-user-interface-issues.md)   
 [Classe de COleStreamFile](../mfc/reference/colestreamfile-class.md)   
 [COleDocument, classe](../mfc/reference/coledocument-class.md)
