---
title: -GT (stockage Local des threads de fibres sécurisées prise en charge) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFiberSafeOptimizations
- /gt
dev_langs:
- C++
helpviewer_keywords:
- /GT compiler option [C++]
- GT compiler option [C++]
- thread-local storage
- static thread-local storage and fiber safety
- -GT compiler option [C++]
- fiber-safe static thread-local storage compiler option [C++]
ms.assetid: 071fec79-c701-432b-9970-457344133159
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 493199cf4d5e66a866fbaa87aafc4098c3114cf6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373827"
---
# <a name="gt-support-fiber-safe-thread-local-storage"></a>/GT (Prendre en charge le stockage local des threads avec fibres sécurisées)
Prend en charge la sécurité des fibres pour les données allouées à l’aide du stockage local des threads statique, autrement dit, les données allouées avec `__declspec(thread)`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/GT  
```  
  
## <a name="remarks"></a>Notes  
 Données déclaré avec `__declspec(thread)` est référencé via un tableau le stockage local des threads (TLS). Le tableau TLS est un tableau d’adresses que le système gère pour chaque thread. Chaque adresse de ce tableau indique l’emplacement des données de stockage local des threads.  
  
 Une fibre est un objet léger qui se compose d’une pile et un contexte de Registre et permettre être planifié sur des threads différents. Une fibre peut s’exécuter sur n’importe quel thread. Car une fibre peut être transférée et redémarrée ultérieurement sur un autre thread, l’adresse du tableau TLS ne doit pas être mis en cache ou optimisée en tant qu’une sous-expression commune dans un appel de fonction (consultez le [/Og (optimisations globales)](../../build/reference/og-global-optimizations.md) est définie sur Détails). **/GT** évite de telles optimisations.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur le **optimisation** page de propriétés.  
  
4.  Modifier la **activer les optimisations à fibres sécurisées** propriété.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFiberSafeOptimizations%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)