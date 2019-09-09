---
title: Dépannage d'applications isolées C/C++ et d'assemblys côte à côte
ms.date: 11/04/2016
helpviewer_keywords:
- troubleshooting side-by-side assemblies
- troubleshooting isolated applications
- troubleshooting Visual C++
ms.assetid: 3257257a-1f0b-4ede-8564-9277a7113a35
ms.openlocfilehash: 1bd0d7638a8e7f2e3c671229e1f8d118d681e6f4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492573"
---
# <a name="troubleshooting-cc-isolated-applications-and-side-by-side-assemblies"></a>Dépannage d'applications isolées C/C++ et d'assemblys côte à côte

Le chargement d'une application C/C++ peut échouer si les bibliothèques dépendantes sont introuvables. Cet article décrit les raisons les plus courantes de l'échec du chargement d'une application C/C++, et suggère une procédure de résolution des problèmes.

Si le chargement d'une application échoue car le manifeste de l'application stipule une dépendance sur un assembly côte à côte, et que l'assembly n'est pas installé en tant qu'assembly privé dans le même dossier que l'exécutable, ni dans le cache d'assembly natif dans le dossier %WINDIR%\WinSxS\, l'un des messages d'erreur suivants peut s'afficher, selon la version de Windows sur laquelle vous tentez d'exécuter l'application.

- L'application n'a pas réussi à s'initialiser correctement (0xc0000135).

- Cette application n'a pas démarré, car la configuration de l'application est incorrecte. Réinstaller l'application pourrait résoudre ce problème.

- Le système ne peut exécuter le programme spécifié.

Si votre application ne possède aucun manifeste et dépend d'une DLL que Windows ne peut pas trouver dans les emplacements standard de recherche, un message d'erreur semblable au suivant peut afficher :

- Cette application n’a pas pu démarrer car *une dll requise* est introuvable. La réinstallation de cette application peut corriger ce problème.

Si votre application est déployée sur un ordinateur qui ne dispose pas de Visual Studio, et qu'elle s'arrête avec des messages d'erreur semblables aux précédents, vérifiez les points suivants :

1. Suivez les étapes décrites dans [fonctionnement des dépendances d’une application visuelle C++ ](../windows/understanding-the-dependencies-of-a-visual-cpp-application.md). Dependency Walker peut afficher la plupart des dépendances d'une application ou d'une DLL. Si vous constatez que certaines DLL sont manquantes, installez-les sur l'ordinateur sur lequel vous essayez d'exécuter votre application.

1. Le chargeur du système d'exploitation utilise le manifeste de l'application pour charger les assemblys dont dépend l'application. Le manifeste peut être incorporé dans le fichier binaire en tant que ressource ou installé en tant que fichier distinct dans le dossier de l'application. Pour vérifier si le manifeste est incorporé dans le fichier binaire, ouvrez le fichier binaire dans Visual Studio et recherchez RT_MANIFEST dans sa liste de ressources. Si vous ne trouvez pas de manifeste incorporé, recherchez dans le dossier de l’application un fichier nommé, par exemple < binary_name >. \<extension >. manifest.

1. Si votre application dépend d'assemblys côte à côte et qu'un manifeste n'est pas présent, vous devez vous assurer que l'éditeur de liens génère un manifeste pour votre projet. Cochez l’option générer le **manifeste** de l’éditeur de liens dans la boîte de dialogue **Propriétés du projet** pour le projet.

1. Si le manifeste est incorporé dans le fichier binaire, assurez-vous que l'ID de RT_MANIFEST est correct pour ce type de fichier binaire. Pour plus d’informations sur l’ID de ressource à utiliser, consultez [utilisation d’assemblys côte à côte en tant que ressource (Windows)](/windows/win32/SbsCs/using-side-by-side-assemblies-as-a-resource). Si le manifeste est dans un fichier distinct, ouvrez-le dans un éditeur XML ou un éditeur de texte. Pour plus d’informations sur les manifestes et les règles de déploiement, consultez [manifestes](/windows/win32/sbscs/manifests).

   > [!NOTE]
   > Si un manifeste incorporé et un fichier manifeste distinct sont tous les deux présents, le chargeur du système d'exploitation utilise le manifeste incorporé et ignore le fichier distinct. Toutefois, Windows XP fonctionne de manière inverse : le fichier manifeste distinct est utilisé et le manifeste incorporé est ignoré.

1. Nous vous recommandons d'incorporer un manifeste dans chaque DLL car les manifestes externes sont ignorés quand une DLL est chargée via un appel à `LoadLibrary`. Pour plus d’informations, consultez [manifestes d’assembly](/windows/win32/SbsCs/assembly-manifests).

1. Vérifiez que tous les assemblys énumérés dans le manifeste sont correctement installés sur l'ordinateur. Chaque assembly est spécifié dans le manifeste par son nom, son numéro de version et son architecture de processeur. Si votre application dépend d’assemblys côte à côte, vérifiez que ces assemblys sont correctement installés sur l’ordinateur afin que le chargeur du système d’exploitation puisse les trouver, comme décrit dans [séquence de recherche d’assemblys](/windows/win32/SbsCs/assembly-searching-sequence). N'oubliez pas que les assemblys 64 bits ne peuvent pas être chargés dans des processus 32 bits ni exécutés sur des systèmes d'exploitation 32 bits.

## <a name="example"></a>Exemple

Supposons que nous ayons une application, Appl. exe, créée à l’aide C++de Visual. Le manifeste de l'application est soit incorporé dans appl.exe en tant que ressource binaire RT_MANIFEST, qui a un ID égal à 1, soit stocké en tant que fichier distinct appl.exe.manifest. Le contenu de ce manifeste ressemble à ceci :

```
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
  <dependency>
    <dependentAssembly>
      <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"></assemblyIdentity>
    </dependentAssembly>
  </dependency>
</assembly>
```

Ce manifeste indique au chargeur du système d'exploitation que le fichier appl.exe dépend d'un assembly nommé Fabrikam.SxS.Library, version 2.0.20121.0, généré pour une architecture de processeur x86 32 bits. L'assembly côte à côte dépendant peut être installé comme un assembly partagé ou comme un assembly privé.

Dans le cas d'un assembly partagé, le manifeste de l'assembly est installé dans le dossier %WINDIR%\WinSxS\Manifests\. Il identifie l'assembly et répertorie son contenu, c'est-à-dire les DLL qui font partie de l'assembly :

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
   <noInheritable/>
   <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>
   <file name="Fabrikam.Main.dll" hash="3ca5156e8212449db6c622c3d10f37d9adb1ab12" hashalg="SHA1"/>
   <file name="Fabrikam.Helper.dll" hash="92cf8a9bb066aea821d324ca4695c69e55b2d1c2" hashalg="SHA1"/>
</assembly>
```

Les assemblys côte à côte peuvent également utiliser des [fichiers de configuration d’éditeur](/windows/win32/SbsCs/publisher-configuration-files)(également appelés fichiers de stratégie) pour rediriger globalement des applications et des assemblys afin d’utiliser une version d’un assembly côte à côte au lieu d’une autre version du même assembly. Vous pouvez vérifier les stratégies pour un assembly partagé dans le dossier %WINDIR%\WinSxS\Policies\. Voici un exemple de fichier de stratégie :

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">

   <assemblyIdentity type="win32-policy" name="policy.2.0.Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>
   <dependency>
      <dependentAssembly>
         <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>
         <bindingRedirect oldVersion="2.0.10000.0-2.0.20120.99" newVersion="2.0.20121.0"/>
      </dependentAssembly>
   </dependency>
</assembly>
```

Ce fichier de stratégie spécifie que toute application ou tout assembly qui demande la version 2.0.10000.0 de cet assembly doit utiliser à la place la version 2.0.20121.0, qui est la version actuellement installée sur le système. Si une version de l'assembly mentionné dans le manifeste de l'application est spécifiée dans le fichier de stratégie, le chargeur recherche une version de cet assembly spécifiée dans le manifeste dans le dossier %WINDIR%\WinSxS\, et si cette version n'est pas installée, le chargement échoue. Et si la version 2.0.20121.0 de l'assembly n'est pas installée, le chargement échoue pour les applications qui demandent la version 2.0.10000.0 de l'assembly.

Toutefois, l'assembly peut également être installé comme un assembly côte à côte privé dans le dossier de l'application installée. Si le système d'exploitation ne parvient pas à trouver l'assembly sous la forme d'un assembly partagé, il le cherche sous la forme d'un assembly privé, dans l'ordre suivant :

1. Recherchez dans le dossier de l’application un fichier manifeste portant le \<nom AssemblyName >. manifest. Dans cet exemple, le chargeur essaie de trouver Fabrikam.SxS.Library.manifest dans le dossier qui contient appl.exe. S'il trouve ce manifeste, le chargeur charge l'assembly à partir du dossier de l'application. Si l'assembly est introuvable, le chargement échoue.

1. Essayez d’ouvrir le \\dossier <\>AssemblyName \ dans le dossier qui contient Appl. exe, et si \\< AssemblyName\>\ Exists, essayez de charger un fichier manifeste portant le nom \<AssemblyName >. manifeste à partir de ce dossier. Si le manifeste est trouvé, le chargeur charge l’assembly à partir \\du dossier\>< AssemblyName \. Si l'assembly est introuvable, le chargement échoue.

Pour plus d’informations sur la façon dont le chargeur recherche les assemblys dépendants, consultez [séquence de recherche](/windows/win32/SbsCs/assembly-searching-sequence)d’assemblys. Si le chargeur ne parvient pas à trouver un assembly dépendant sous la forme d'un assembly privé, le chargement échoue et le message « Le système ne peut exécuter le programme spécifié » s'affiche. Pour résoudre cette erreur, assurez-vous que les assemblys dépendants (et les DLL qui en font partie) sont installés sur l'ordinateur en tant qu'assemblys privés ou partagés.

## <a name="see-also"></a>Voir aussi

[Concepts d’applications isolées et d’assemblys côte à côte](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Génération d’applications isolées et d’assemblys côte à côte C/C++](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
