---
title: -INTEGRITYCHECK (exiger la vérification de Signature) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 997e3f5bb79ee3cbfa95c5762b0d3e998c56f362
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374243"
---
# <a name="integritycheck-require-signature-check"></a>/INTEGRITYCHECK (Exiger la vérification de la signature)
Spécifie que la signature numérique de l’image binaire doit être vérifiée au moment du chargement.  
  
```  
/INTEGRITYCHECK[:NO]  
```  
  
## <a name="remarks"></a>Notes  
 Par défaut, **/INTEGRITYCHECK** est désactivée.  
  
 Le **/INTEGRITYCHECK** jeux d’option, dans l’en-tête PE du fichier DLL ou du fichier exécutable, un indicateur pour le Gestionnaire de mémoire vérifier une signature numérique afin de charger l’image dans Windows. Cette option doit être définie pour les DLL 32 bits et 64 bits qui implémentent de code en mode noyau chargé par certaines fonctionnalités de Windows et sont recommandées pour tous les pilotes de périphériques sur Windows Vista, [!INCLUDE[win7](../../build/includes/win7_md.md)], [!INCLUDE[win8](../../build/reference/includes/win8_md.md)], [!INCLUDE[winsvr08](../../build/reference/includes/winsvr08_md.md)], et [!INCLUDE[winserver8](../../build/reference/includes/winserver8_md.md)]. Les versions de Windows antérieures à Windows Vista ignorent cet indicateur. Pour plus d’informations, consultez [les fichiers forcé l’intégrité de signature de PE (Portable Executable)](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx).  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Développez le **propriétés de Configuration** nœud.  
  
3.  Développez le **l’éditeur de liens** nœud.  
  
4.  Sélectionnez le **ligne de commande** page de propriétés.  
  
5.  Dans **des Options supplémentaires**, entrez `/INTEGRITYCHECK` ou `/INTEGRITYCHECK:NO`.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)   
 [Fichiers de l’intégrité de signature de PE (Portable Executable) forcé](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)   
 [Procédure pas à pas de signature du Code en Mode noyau](http://msdn.microsoft.com/windows/hardware/gg487328.aspx)   
 [DLL AppInit dans Windows 7 et Windows Server 2008](http://msdn.microsoft.com/windows/hardware/gg463040.aspx)