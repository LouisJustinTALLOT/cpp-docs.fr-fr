---
title: partial (Extensions du composant C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- partial_CPP
dev_langs:
- C++
helpviewer_keywords:
- partial
- C++/CX, partial
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 71c0fc9739e7ef8e1e68c5678ce56fcec4a250c1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880177"
---
# <a name="partial--c-component-extensions"></a>partial (extensions de composant C++)
Le `partial` (mot clé) permettent aux différentes parties de la même classe ref pour être créé indépendamment et dans différents fichiers.  
  
## <a name="all-runtimes"></a>Tous les runtimes  
 (Cette fonctionnalité de langage s’applique uniquement à l’exécution de Windows).  
  
## <a name="windows-runtime"></a>Windows Runtime  
 Pour une classe ref qui a deux définitions partielles, le `partial` (mot clé) est appliqué à la première occurrence de la définition de, et cela s’effectue généralement par le code généré automatiquement, afin qu’un codeur humain n’utilise pas le mot clé très souvent. Pour toutes les définitions partielles suivantes de la classe, omettez le `partial` modificateur à partir de la *clé-classe* identificateur mot clé et de la classe. Lorsque le compilateur rencontre une classe ref précédemment défini et identificateur de classe mais non `partial` (mot clé), elle combine toutes les parties de la définition de classe ref dans une seule définition.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
partial class-key identifier {  
   /* The first part of the partial class definition. 
      This is typically auto-generated */  
}  
// ...  
class-key identifier {  
   /* The subsequent part(s) of the class definition. The same 
      identifier is specified, but the "partial" keyword is omitted. */  
}  
```  
  
### <a name="parameters"></a>Paramètres  
 *clé de la classe*  
 Un mot clé qui déclare une classe ou un struct qui est pris en charge par le Windows Runtime. Soit `ref class`, `value class`, `ref struct`, ou `value struct`.  
  
 *identifier*  
 Le nom du type défini.  
  
### <a name="remarks"></a>Notes  
 Une classe partielle prend en charge les scénarios où vous modifiez une partie d’une définition de classe dans un fichier et logiciel de génération de code automatique, par exemple, le concepteur XAML, modifie le code dans la même classe dans un autre fichier. En utilisant une classe partielle, vous pouvez empêcher le Générateur de code automatique de remplacer votre code. Dans un projet Visual Studio, le modificateur `partial` est appliqué automatiquement au fichier généré.  
  
 Contenu : À deux exceptions près, une définition de classe partielle peut contenir tout ce que la définition de classe complète peut contenir si le `partial` (mot clé) a été omis. Toutefois, vous ne pouvez pas spécifier l’accessibilité de la classe (par exemple, `public partial class X { ... };`), ou un `declspec`.  
  
 Utilisé dans une définition de classe partielle pour des spécificateurs d’accès *identificateur* n’affectent pas l’accessibilité par défaut dans une définition de classe partielle ou complète pour *identificateur*. Les définitions inline des données membres statiques sont autorisées.  
  
 Déclaration : Une définition partielle d’une classe *identificateur* présente uniquement le nom *identificateur*, mais *identificateur* ne peut pas être utilisé d’une manière qui requiert une classe définition. Le nom *identificateur* ne peut pas être utilisé pour connaître la taille de *identificateur*, ou utiliser une base ou un membre de *identificateur* jusqu'à ce qu’une fois que le compilateur rencontre la définition complète de *identificateur*.  
  
 Nombre et l’ordre : il peut y avoir zéro ou plusieurs définitions de classe partielle pour *identificateur*. Chaque définition de classe partielle de *identificateur* doit précéder lexicalement la seule définition complète de *identificateur* (s’il existe une définition complète ; sinon, la classe ne peut pas être utilisée, sauf comme si déclaré en avant), mais ne doivent pas précéder les déclarations anticipées de *identificateur*. Toutes les clés de classe doivent correspondre.  
  
 Complète la définition de : dans la phase de définition complète de la classe *identificateur*, le comportement est le même que si la définition de *identificateur* a déclaré toutes les classes de base, des membres, etc. dans l’ordre dans lequel elles ont été rencontrés et définies dans les classes partielles.  
  
 Modèles : Une classe partielle ne peut pas être un modèle.  
  
 Génériques : Une classe partielle peut être un type générique si la définition complète peut être générique. Mais chaque classe partielle et complet doit avoir exactement les mêmes paramètres génériques, y compris les noms de paramètres formels.  
  
 Pour plus d’informations sur l’utilisation de la `partial` (mot clé), consultez [Classes partielles (C + c++ / CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023).  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
 (Cette fonctionnalité de langage ne s’applique pas pour le Common Language Runtime).  
  
## <a name="see-also"></a>Voir aussi  
 [Classes partielles (C + c++ / CX)](http://go.microsoft.com/fwlink/p/?LinkId=249023)