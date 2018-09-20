---
title: Directives pragma et mot clé _pragma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#pragma'
dev_langs:
- C++
helpviewer_keywords:
- '#pragma directives, C/C++'
- __pragma keyword
- pragma directives, C/C++
- pragmas, C/C++
- preprocessor
- pragmas
- preprocessor, pragmas
- pragma directives (#pragma)
ms.assetid: 9867b438-ac64-4e10-973f-c3955209873f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f195a553c29c8a1cd0ef57f82c9f57a1f3672048
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405292"
---
# <a name="pragma-directives-and-the-pragma-keyword"></a>Directives pragma et mot clé _Pragma
Les directives pragma spécifient des fonctionnalités de compilateur spécifiques à l’ordinateur ou au système d’exploitation. Le **_pragma** mot clé, qui est spécifique au compilateur de Microsoft, vous permet de coder des directives pragma dans des définitions de macro.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma token-string  
__pragma(token-string)  
```  
  
## <a name="remarks"></a>Notes  
 
Chaque implémentation de C et C++ prend en charge des fonctionnalités spécifiques de son ordinateur hôte ou de son système d’exploitation. Certains programmes, par exemple, doivent exercer un contrôle précis des zones de mémoire où les données sont placées, ou contrôler la façon dont certaines fonctions reçoivent les paramètres. Le **#pragma** directives offrent un moyen pour chaque compilateur d’offrir des fonctionnalités propres de machine et de système d’exploitation tout en conservant une compatibilité globale avec les langages C et C++.  
  
Les pragmas sont spécifiques à l'ordinateur ou au système d'exploitation, par définition, et sont généralement différents pour chaque compilateur. Les pragmas peuvent être utilisés dans les instructions conditionnelles pour fournir de nouvelles fonctionnalités de préprocesseur ou pour fournir des informations définies par l'implémentation au compilateur.  
  
`token-string` est une série de caractères qui fournit à un compilateur spécifique l'instruction et les arguments, le cas échéant. Le signe dièse (**#**) doit être le premier caractère autre qu’un espace blanc sur la ligne qui contient le pragma ; blancs peuvent séparer le signe dièse et le mot « pragma ». Suivant **#pragma**, saisissez un texte que le traducteur peut analyser en tant que jetons de prétraitement. L’argument **#pragma** est soumis à une expansion macro.  
  
Si le compilateur recherche un pragma qu'il ne reconnaît pas, il émet un avertissement et continue la compilation.  
  
Les compilateurs Microsoft C et C++ reconnaissent les pragmas suivants :  
  
||||  
|-|-|-|  
|[alloc_text](../preprocessor/alloc-text.md)|[auto_inline](../preprocessor/auto-inline.md)|[bss_seg](../preprocessor/bss-seg.md)|  
|[check_stack](../preprocessor/check-stack.md)|[code_seg](../preprocessor/code-seg.md)|[commentaire](../preprocessor/comment-c-cpp.md)|  
|[component](../preprocessor/component.md)|[se conformer](../preprocessor/conform.md) <sup>1</sup>|[const_seg](../preprocessor/const-seg.md)|  
|[data_seg](../preprocessor/data-seg.md)|[deprecated](../preprocessor/deprecated-c-cpp.md)|[detect_mismatch](../preprocessor/detect-mismatch.md)|  
|[fenv_access](../preprocessor/fenv-access.md)|[float_control](../preprocessor/float-control.md)|[fp_contract](../preprocessor/fp-contract.md)|  
|[function](../preprocessor/function-c-cpp.md)|[hdrstop](../preprocessor/hdrstop.md)|[include_alias](../preprocessor/include-alias.md)|  
|[init_seg](../preprocessor/init-seg.md) <sup>1</sup>|[inline_depth](../preprocessor/inline-depth.md)|[inline_recursion](../preprocessor/inline-recursion.md)|  
|[intrinsic](../preprocessor/intrinsic.md)|[boucle](../preprocessor/loop.md) <sup>1</sup>|[make_public](../preprocessor/make-public.md)|  
|[Gérés](../preprocessor/managed-unmanaged.md)|[message](../preprocessor/message.md)||  
|[omp](../preprocessor/omp.md)|[once](../preprocessor/once.md)||  
|[optimize](../preprocessor/optimize.md)|[pack](../preprocessor/pack.md)|[pointers_to_members](../preprocessor/pointers-to-members.md) <sup>1</sup>|  
|[pop_macro](../preprocessor/pop-macro.md)|[push_macro](../preprocessor/push-macro.md)|[region, endregion](../preprocessor/region-endregion.md)|  
|[runtime_checks](../preprocessor/runtime-checks.md)|[section](../preprocessor/section.md)|[setlocale](../preprocessor/setlocale.md)|  
|[strict_gs_check](../preprocessor/strict-gs-check.md)|[non managé](../preprocessor/managed-unmanaged.md)|[vtordisp](../preprocessor/vtordisp.md) <sup>1</sup>|  
|[warning](../preprocessor/warning.md)|||  
  
 1. Pris en charge uniquement par le compilateur C++.  
  
## <a name="pragmas-and-compiler-options"></a>Pragmas et options du compilateur  
 
Certains pragmas fournissent les mêmes fonctionnalités que les options du compilateur. Lorsqu'un pragma est rencontré dans le code source, il remplace le comportement spécifié par l'option du compilateur. Par exemple, si vous avez spécifié [/Zp8](../build/reference/zp-struct-member-alignment.md), vous pouvez remplacer ce paramètre de compilateur des sections spécifiques du code avec [pack](../preprocessor/pack.md):  
  
```  
cl /Zp8 ...  
  
<file> - packing is 8  
// ...  
#pragma pack(push, 1) - packing is now 1  
// ...  
#pragma pack(pop) - packing is 8  
</file>  
```  
  
## <a name="the-pragma-keyword"></a>Mot clé __pragma()  
 
**Spécifique à Microsoft**  
  
Le compilateur prend également en charge la **_pragma** mot clé, qui a les mêmes fonctionnalités que le **#pragma** directive, mais peut être utilisé inline dans une définition de macro. Le **#pragma** directive ne peut pas être utilisée dans une définition de macro, car le compilateur interprète le signe dièse ('#') dans la directive pour être le [opérateur d’enchaînement (#)](../preprocessor/stringizing-operator-hash.md).  
  
L’exemple de code suivant montre comment la **_pragma** mot clé peut être utilisé dans une macro. Ce code est extrait de l'en-tête mfcdual.h de l'exemple CDUAL dans « Exemples de prise en charge COM du compilateur » :  
  
```  
#define CATCH_ALL_DUAL \  
CATCH(COleException, e) \  
{ \  
_hr = e->m_sc; \  
} \  
AND_CATCH_ALL(e) \  
{ \  
__pragma(warning(push)) \  
__pragma(warning(disable:6246)) /*disable _ctlState prefast warning*/ \  
AFX_MANAGE_STATE(pThis->m_pModuleState); \  
__pragma(warning(pop)) \  
_hr = DualHandleException(_riidSource, e); \  
} \  
END_CATCH_ALL \  
return _hr; \  
```  
  
**Fin spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 
[Informations de référence sur le préprocesseur C/C++](../preprocessor/c-cpp-preprocessor-reference.md)<br/>
[Pragmas C](../c-language/c-pragmas.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)