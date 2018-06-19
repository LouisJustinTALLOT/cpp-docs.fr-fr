---
title: -DV (désactiver les déplacements de Construction) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /vd
dev_langs:
- C++
helpviewer_keywords:
- -vd0 compiler option [C++]
- vd1 compiler option [C++]
- /vdn (Disable Construction Displacement) compiler option
- constructor displacements
- vtordisp fields
- /vd0 compiler option [C++]
- -vd1 compiler option [C++]
- /vd1 compiler option [C++]
- displacements compiler option
- vd0 compiler option [C++]
- Disable Construction Displacements compiler option
ms.assetid: 93258964-14d7-4b1c-9cbc-d6f4d74eab69
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6a7b9bacc95c668c1c0f59a3dba172d58c607d2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377595"
---
# <a name="vd-disable-construction-displacements"></a>/vd (Désactiver les déplacements de construction)
## <a name="syntax"></a>Syntaxe  
  
```  
/vdn  
```  
  
## <a name="arguments"></a>Arguments  
 `0`  
 Supprime le membre de déplacement de constructeur/destructeur vtordisp. Choisissez cette option uniquement si vous êtes certain que tous les constructeurs de classe et les destructeurs appellent virtuels virtuellement les fonctions.  
  
 `1`  
 Permet la création de membres de déplacement de constructeur/destructeur vtordisp masqué. Ce choix est la valeur par défaut.  
  
 `2`  
 Vous pouvez utiliser [opérateur dynamic_cast](../../cpp/dynamic-cast-operator.md) sur un objet en cours de construction. Par exemple, un dynamic_cast d’une classe de base virtuelle vers une classe dérivée.  
  
 **/ vd2** ajoute un champ vtordisp lorsque vous utilisez une base virtuelle avec des fonctions virtuelles. **/ vd1** doit être suffisante. Les plus courants de cas où **/vd2** est nécessaire est lorsque la seule fonction virtuelle dans votre base virtuelle est un destructeur.  
  
## <a name="remarks"></a>Notes  
 Ces options s’appliquent uniquement au code C++ qui utilise des bases virtuelles.  
  
 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] implémente la prise en charge de déplacement de construction C++ dans les situations où l’héritage virtuel est utilisé. Les déplacements de construction résout le problème créé lorsqu’une fonction virtuelle, déclarée dans une base virtuelle et de substitution dans une classe dérivée, est appelée à partir d’un constructeur pendant la construction d’une classe plus dérivée.  
  
 Le problème est que la fonction virtuelle peut être passée incorrect `this` pointeur en conséquence des différences entre les déplacements vers le serveur virtuel de base d’une classe et les déplacements vers les classes dérivées. La solution fournit un ajustement de déplacement de construction unique, appelé champ vtordisp, pour chaque base virtuelle d’une classe.  
  
 Par défaut, les champs vtordisp sont introduits chaque fois que le code définit des destructeurs et des constructeurs définis par l’utilisateur et qu’il remplace également des fonctions virtuelles des bases virtuelles.  
  
 Ces options affectent l’ensemble des fichiers sources. Utilisez [vtordisp](../../preprocessor/vtordisp.md) à supprimer, puis réactiver les champs vtordisp classe par classe.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur la page de propriétés **Ligne de commande** .  
  
4.  Tapez l'option de compilateur dans la zone **Options supplémentaires** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)