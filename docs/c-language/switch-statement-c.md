---
title: switch, instruction (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- switch
dev_langs:
- C++
helpviewer_keywords:
- switch keyword [C]
ms.assetid: fbede014-23bd-4ab1-8094-c8d9d9cb963a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0fab1f385556346ff81f89e94d20c5f416ff67b9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392157"
---
# <a name="switch-statement-c"></a>switch, instruction (C)
Les instructions `switch` et **case** aident à contrôler les opérations conditionnelles et de création de branche complexes. L'instruction `switch` transfère le contrôle à une instruction dans son corps.  
  
## <a name="syntax"></a>Syntaxe  
 *selection-statement* :  
 **switch (** *expression* **)** *statement*  
  
 *labeled-statement* :  
 **case**  *constant-expression*  **:**  *statement*  
  
 **default :**  *statement*  
  
 Le contrôle passe à l’instruction dont **case** *constant-expression* correspond à la valeur de **switch (** *expression* **)**. L’instruction `switch` peut inclure plusieurs instances de **case**, mais deux constantes case dans la même instruction `switch` ne peuvent pas avoir la même valeur. L’exécution du corps de l’instruction commence à l’instruction sélectionnée et continue jusqu’à la fin du corps ou jusqu’à ce qu’une instruction **break** transfère le contrôle hors du corps.  
  
 L'utilisation de l'instruction `switch` ressemble généralement à ceci :  
  
 `switch` ( *expression* )  
  
 **{**  
  
 *declarations*  
  
 .  
  
 .  
  
 .  
  
 **case** *constant-expression* **:**  
  
 *instructions exécutées si l’expression est égale à la*  
  
 *valeur de constant-expression*  
  
 .  
  
 .  
  
 .  
  
 **break;**  
  
 **default :**  
  
 *instructions exécutées si l’expression n’est pas égale à*  
  
 *tout case constant-expression*  
  
 **}**  
  
 Vous pouvez utiliser l’instruction **break** pour terminer le traitement d’un cas particulier dans l’instruction `switch` et pour créer une branche à la fin de l’instruction `switch`. Sans **break**, le programme continue au cas suivant et exécute les instructions jusqu’à ce qu’il rencontre un **break** ou qu’il atteigne la fin de l’instruction. Dans certaines situations, cette continuation peut être souhaitable.  
  
 L’instruction **default** est exécutée si aucun **case** *constant-expression* n’est égale à la valeur de **switch (** *expression* **)**. Si l’instruction **default** est omise et qu’aucun **case** correspondant n’est trouvé, aucune des instructions dans le corps de `switch` n’est exécutée. Il peut y avoir au plus une instruction **default**. Il n’est pas obligatoire que l’instruction **default** soit à la fin ; elle peut apparaître n’importe où dans le corps de l’instruction `switch`. Une étiquette **case** ou **default** ne peut apparaître que dans une instruction `switch`.  
  
 Le type de `switch` *expression* et **case** *constant-expression* doit être intégral. La valeur de chaque **case** *constant-expression* doit être unique dans le corps de l’instruction.  
  
 Les étiquettes **case** et **default** du corps de l’instruction `switch` sont significatives uniquement lors du test initial qui détermine où commence l’exécution dans le corps de l’instruction. Les instructions switch peuvent être imbriquées. Toutes les variables statiques sont initialisées avant l'exécution dans les instructions `switch`.  
  
> [!NOTE]
>  Des déclarations peuvent apparaître au début de l'instruction composée formant le corps de `switch`, mais les initialisations incluses dans les déclarations ne sont pas exécutées. L'instruction `switch` transfère le contrôle directement à une instruction exécutable dans le corps, en ignorant les lignes qui contiennent des initialisations.  
  
 L'exemples suivant illustre des instructions `switch` :  
  
```  
switch( c )   
{  
    case 'A':  
        capa++;  
    case 'a':  
        lettera++;  
    default :  
        total++;  
}  
```  
  
 Les trois instructions du corps de `switch` dans cet exemple sont exécutées si `c` est égal à `'A'`, car une instruction **break** n’apparaît pas avant le cas suivant. Le contrôle d'exécution est transféré à la première instruction (`capa++;`) et continue dans l'ordre à travers le reste du corps. Si `c` est égal à `'a'`, `lettera` et `total` sont incrémentés. Seul `total` est incrémenté si `c` n'est pas égal à `'A'` ou `'a'`.  
  
```  
switch( i )   
{  
    case -1:  
        n++;  
        break;  
    case 0 :  
        z++;  
        break;  
    case 1 :  
        p++;  
        break;  
}  
```  
  
 Dans cet exemple, une instruction **break** suit chaque instruction du corps de `switch`. L’instruction **break** force une sortie du corps d’instruction après l’exécution d’une instruction. Si `i` est égal à -1, seul `n` est incrémenté. Le **break** suivant l’instruction `n++;` provoque le passage du contrôle d’exécution hors du corps d’instruction, ignorant les instructions restantes. De même, si `i` est égal à 0, seul `z` est incrémenté ; si `i` est égal à 1, seul `p` est incrémenté. L’instruction **break** finale n’est pas strictement nécessaire, car le contrôle passe hors du corps à la fin de l’instruction composée, mais elle est incluse pour des raisons de sécurité.  
  
 Une même instruction peut porter plusieurs étiquettes **case**, comme illustré dans l’exemple suivant :  
  
```  
case 'a' :  
case 'b' :  
case 'c' :  
case 'd' :  
case 'e' :  
case 'f' :  hexcvt(c);  
```  
  
 Dans cet exemple, si *constant-expression* est égale à toute lettre comprise entre `'a'` et `'f'`, la fonction `hexcvt` est appelée.  
  
 **Section spécifique à Microsoft**  
  
 Microsoft C ne limite pas le nombre de valeurs de cas dans une instruction `switch`. Le nombre est limité uniquement par la mémoire disponible. C ANSI requiert qu'au moins 257 étiquettes soient autorisées dans une instruction `switch`.  
  
 Par défaut pour Microsoft C, les extensions Microsoft sont activées. Utilisez l’option du compilateur /Za pour désactiver ces extensions.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [switch, instruction (C++)](../cpp/switch-statement-cpp.md)