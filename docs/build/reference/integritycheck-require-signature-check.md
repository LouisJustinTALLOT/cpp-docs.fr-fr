---
title: -INTEGRITYCHECK (exiger la vérification de Signature) | Microsoft Docs
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
ms.openlocfilehash: 5a10594391b0f3be490608f7dfa006b0c32aa2e0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609278"
---
# <a name="integritycheck-require-signature-check"></a>/INTEGRITYCHECK (Exiger la vérification de la signature)
Spécifie que la signature numérique de l’image binaire doit être vérifiée au moment du chargement.  
  
```  
/INTEGRITYCHECK[:NO]  
```  
  
## <a name="remarks"></a>Notes  
 Par défaut, **/INTEGRITYCHECK** est désactivé.  
  
 Le **/INTEGRITYCHECK** groupes d’options, dans l’en-tête PE du fichier DLL ou du fichier exécutable, un indicateur pour le Gestionnaire de mémoire vérifier une signature numérique afin de charger l’image dans Windows. Cette option doit être définie pour les DLL 32 bits et 64 bits qui implémentent le code en mode noyau chargé par certaines fonctionnalités de Windows et est recommandée pour tous les pilotes de périphériques sur Windows Vista, Windows 7, Windows 8, Windows Server 2008 et Windows Server 2012. Les versions de Windows antérieures à Windows Vista ignorent cet indicateur. Pour plus d’informations, consultez [forcé l’intégrité de signature de fichiers Portable Executable (PE)](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx).  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Développez le nœud **Propriétés de configuration**.  
  
3.  Développez le **l’éditeur de liens** nœud.  
  
4.  Sélectionnez le **ligne de commande** page de propriétés.  
  
5.  Dans **des Options supplémentaires**, entrez `/INTEGRITYCHECK` ou `/INTEGRITYCHECK:NO`.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)   
 [Forcé l’intégrité signature de fichiers Portable Executable (PE)](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)   
 [Procédure pas à pas de signature du Code en Mode noyau](http://msdn.microsoft.com/windows/hardware/gg487328.aspx)   
 [DLL AppInit dans Windows 7 et Windows Server 2008](http://msdn.microsoft.com/windows/hardware/gg463040.aspx)