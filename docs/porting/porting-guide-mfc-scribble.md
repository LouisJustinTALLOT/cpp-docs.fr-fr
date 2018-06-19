---
title: 'Guide du portage : Scribble MFC | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8ddb517d-89ba-41a1-ab0d-4d2c6d9047e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe0ae0580be4ab062e3ff7ee0cedfb42e201272d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845906"
---
# <a name="porting-guide-mfc-scribble"></a>Guide du portage : Scribble MFC
Cette rubrique est la première d’une série de rubriques qui présentent le processus de mise à niveau de projets Visual C++ créés dans des versions antérieures de Visual Studio vers Visual Studio 2017. Ces rubriques abordent la mise à niveau en commençant par un exemple de projet très simple, avant de traiter des exemples de projets un peu plus complexes. Dans cette rubrique, nous effectuerons la mise à niveau d'un projet spécifique, appelé Scribble MFC. C'est un exemple qui nous permettra d'aborder les notions de base de la mise à niveau de projets C++.  
  
 Chaque version de Visual Studio présente des incompatibilités susceptibles de compliquer la migration du code d'une version antérieure de Visual Studio vers une version plus récente. Des modifications sont parfois à effectuer directement dans votre code et, dans ce cas, vous devez recompiler et mettre à jour le code. Des modifications peuvent également être nécessaires dans les fichiers projet. Quand vous ouvrez un projet qui a été créé avec une version antérieure de Visual Studio, Visual Studio vous demande automatiquement s'il faut mettre à jour le projet ou la solution vers la dernière version. En général, ces outils mettent à niveau les fichiers projet uniquement, sans modifier le code source.  
  
## <a name="mfc-scribble"></a>Scribble MFC  
 Scribble MFC est un exemple bien connu qui a déjà été utilisé dans de nombreuses versions différentes de Visual C++. C'est une application de dessin simple qui illustre certaines fonctionnalités de base de MFC. L'application est disponible dans différentes versions, y compris en code managé et en code natif. Pour cet exemple, nous avons trouvé une ancienne version de Scribble en code natif de Visual Studio 2005 et l’avons ouverte dans Visual Studio 2017.  
  
 Avant de tenter la mise à niveau, vérifiez que la charge de travail Windows Desktop est installée. Ouvrez le programme d’installation de Visual Studio (vs_installer.exe). L’une des façons d’ouvrir le programme d’installation consiste à choisir Fichier | Nouveau projet et à faire défiler l’écran vers le bas de la liste des modèles installés jusqu’à « Ouvrir le programme d’installation de Visual Studio ». Après avoir ouvert le programme d’installation, vous verrez toutes les charges de travail disponibles. Si la case associée à la charge de travail Windows Desktop n’est pas cochée, sélectionnez-la, puis cliquez sur le bouton Modifier au bas de la fenêtre. 


 Sauvegardez ensuite l’ensemble de la solution et tout son contenu. 
 
 Enfin, nous avons dû choisir la méthode de mise à niveau. Pour les projets et solutions plus complexes qui n'ont pas été mis à niveau récemment, prévoyez d'effectuer la mise à niveau d'une seule version de Visual Studio à la fois. Vous pouvez ainsi déterminer précisément la version de Visual Studio qui a introduit un problème. Pour un projet simple, il vaut mieux l'ouvrir dans la version la plus récente de Visual Studio et laisser l'Assistant convertir automatiquement le projet. Si cela ne fonctionne pas, essayez de mettre à niveau une version à la fois, si vous avez accès aux versions appropriées de Visual Studio.  
  
 Notez que vous pouvez aussi exécuter devenv avec l'option `/Upgrade` sur la ligne de commande au lieu d'utiliser l'Assistant pour mettre à niveau vos projets. Consultez [/Upgrade (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe). Cette méthode est utile pour automatiser le processus de mise à niveau d'un grand nombre de projets.  
  
### <a name="step-1-converting-the-project-file"></a>Étape 1. Conversion du fichier projet  
 Quand vous ouvrez un ancien fichier projet dans Visual Studio 2017, Visual Studio propose de le convertir vers la version la plus récente, ce que nous avons choisi de faire. La boîte de dialogue suivante s'est affichée :  
  
 ![Voir les modifications apportées au projet et à la solution](../porting/media/scribbleprojectupgrade.PNG "ScribbleProjectUpgrade")  
  
 Une erreur s'est produite. Le message nous informe que la cible Itanium n'est pas disponible et ne sera donc pas convertie.  
  
```Output  
Platform 'Itanium' is missing from this project. All the configurations and their file configuration settings specific to this platform will be ignored. If you want this platform converted, please make sure you have the corresponding platform installed under '%vctargetpath%\platforms\Itanium'.Continue to convert this project without this platform?  
```  
  
 Au moment de la création du projet Scribble précédent, Itanium était une plateforme cible importante. La plateforme Windows ne prenant plus en charge Itanium, nous avons choisi de continuer sans la prise en charge de la plateforme Itanium.  
  
 Visual Studio affiche ensuite un rapport de migration qui répertorie tous les problèmes rencontrés avec l'ancien fichier projet.  
  
 ![Rapport de mise à niveau](../porting/media/scribblemigrationreport.PNG "ScribbleMigrationReport")  
  
 Dans ce cas, les problèmes signalés étaient tous des avertissements, et Visual Studio a effectué les modifications appropriées dans le fichier projet. La grande différence en ce qui concerne le projet est que l'outil de build utilisé est maintenant msbuild au lieu de vcbuild. Cette modification a été introduite dans Visual Studio 2010. D'autres modifications ont été apportées, notamment une réorganisation de la séquence d'éléments dans le fichier projet. Aucun des problèmes signalés ne nécessitait une attention particulière pour ce projet simple.  
  
### <a name="step-2-getting-it-to-build"></a>Étape 2. Préparation de la build  
 Avant de générer la build, nous vérifions l'ensemble d'outils de plateforme pour savoir quelle version du compilateur est utilisée par le système de projet. Dans la boîte de dialogue Propriétés du projet, sous **Propriétés de configuration**, dans la catégorie **Général**, examinez la propriété **Ensemble d’outils de plateforme**. La propriété indique la version de Visual Studio et le numéro de version des outils de plateforme, qui est ici v141 pour la version Visual Studio 2017 des outils. Quand vous convertissez un projet qui a été initialement compilé avec Visual C++ 2010, 2012, 2013 ou 2015, l’ensemble d’outils n’est pas automatiquement mis à jour vers la version Visual Studio 2017.   
  
  Pour passer au format Unicode, affichez les propriétés du projet, sous **Propriétés de configuration**, choisissez la section **Général** et recherchez la propriété **Jeu de caractères**. Remplacez **Utiliser le jeu de caractères multioctet (MBCS)** par **Utiliser le jeu de caractères Unicode**. Avec cette modification, les macros _UNICODE et UNICODE sont maintenant définies alors que la macro _MBCS ne l’est pas. Vous pouvez vérifier cela dans la boîte de dialogue des propriétés sous la catégorie **C/C++** de la propriété **Ligne de commande**.  
  
```Output  
/GS /analyze- /W4 /Zc:wchar_t /Zi /Gm- /Od /Fd".\Debug\vc141.pdb" /Zc:inline /fp:precise /D "_AFXDLL" /D "WIN32" /D "_DEBUG" /D "_WINDOWS" /D "_UNICODE" /D "UNICODE" /errorReport:prompt /WX /Zc:forScope /Gd /Oy- /MDd /Fa".\Debug\" /EHsc /nologo /Fo".\Debug\" /Fp".\Debug\Scribble.pch" /diagnostics:classic 
```  
  
 Bien que le projet Scribble n'a pas été configuré pour être compilé avec des caractères Unicode, il a déjà été écrit avec TCHAR au lieu de char. Il n'y a donc pas de modification à apporter. Le projet a été compilé correctement avec le jeu de caractères Unicode.  
  
 Générez à présent la solution. Dans la fenêtre Sortie, le compilateur nous indique que _WINNT32_WINNT n’est pas spécifié :  
  
```Output  
_WIN32_WINNT not defined. Defaulting to _WIN32_WINNT_MAXVER (see WinSDKVer.h)  
```  
  
 Ceci n'est pas une erreur, mais un avertissement très fréquent pendant la mise à niveau d'un projet Visual C++. Il s'agit de la macro qui définit la version de Windows la plus ancienne sur laquelle notre application s'exécutera. Si nous ignorons l'avertissement, nous acceptons la valeur par défaut, _WIN32_WINNT_MAXVER, qui correspond à la version actuelle de Windows. Pour obtenir un tableau des valeurs possibles, consultez [Utilisation des en-têtes Windows](https://msdn.microsoft.com/en-us/library/aa383745.aspx). Par exemple, nous pouvons choisir de l'exécuter sur toutes les versions à partir de Vista.  
  
```  
#define _WIN32_WINNT _WIN32_WINNT_VISTA  
```  
  
 Si le code utilise des parties de l'API Windows qui ne sont pas disponibles dans la version de Windows spécifiée avec cette macro, cela produit une erreur de compilateur. Dans le cas de Scribble, il n'y a pas d'erreur.  
  
### <a name="step-3-testing-and-debugging"></a>Étape 3. Test et débogage  
 Comme il n'existe pas de suite de tests, nous avons simplement démarré l'application et testé ses fonctionnalités manuellement via l'interface utilisateur. Nous n'avons observé aucun problème.  
  
### <a name="step-4-improve-the-code"></a>Étape 4. Amélioration du code  
 Maintenant que vous avez effectué la migration vers Visual Studio 2017, vous pouvez apporter quelques modifications pour exploiter au mieux les nouvelles fonctionnalités C++. La version actuelle du compilateur C++ est nettement plus conforme à la norme C++ que les versions précédentes. Si vous envisagez de changer votre code pour le sécuriser ou le rendre davantage compatible avec d’autres compilateurs et systèmes d’exploitation, étudiez les améliorations à apporter.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Scribble était une petite application de bureau Windows, simple, que nous avons pu facilement convertir. De nombreuses applications similaires seront tout aussi faciles à convertir vers la nouvelle version.  La mise à niveau prendra plus de temps pour les applications plus complexes, notamment celles qui contiennent beaucoup plus de lignes de code, du code hérité plus ancien qui n'est sans doute plus conforme aux normes de conception actuelles, plusieurs projets et bibliothèques, des étapes de build personnalisée ou des builds automatisées par script complexes. Continuez avec l’[exemple suivant](../porting/porting-guide-com-spy.md), une application ATL/COM appelée COMSpy.  
  
## <a name="see-also"></a>Voir aussi  
 [Portage et mise à niveau : exemples et études de cas](../porting/porting-and-upgrading-examples-and-case-studies.md)   
 [Exemple suivant : COMSpy](../porting/porting-guide-com-spy.md)
