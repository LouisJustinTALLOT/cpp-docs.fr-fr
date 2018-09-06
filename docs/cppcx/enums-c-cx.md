---
title: Énumérations (C++ / c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 99fbbe28-c1cd-43af-9ead-60f90eba6e68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 725e2b9edb7ba2a84418e900ffb1aafe4c5064af
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758899"
---
# <a name="enums-ccx"></a>Énumérations (C++/CX)
C++ / c++ / CX prend en charge la `public enum class` mot clé, ce qui est analogue à un C++ standard `scoped  enum`. Lorsque vous utilisez un énumérateur qui est déclaré à l'aide du mot clé `public enum class` , vous devez utiliser l'identificateur d'énumération pour limiter chaque valeur de l'énumérateur.  
  
### <a name="remarks"></a>Notes  
 Un `public enum class` qui n'a pas de spécificateur d'accès, tel que `public`, est traité comme un [scoped enum](../cpp/enumerations-cpp.md)C++ standard.  
  
 Un `public enum class` ou `public enum struct` déclaration peut avoir un type sous-jacent de n’importe quel type intégral bien que le Runtime Windows lui-même nécessite que le type soit int32 ou uint32 pour un enum. La syntaxe suivante décrit les éléments d'un `public enum class` ou d'un `public enum struct`.  
  
 Cet exemple montre comment définir une classe d'énumération publique :  
  
 [!code-cpp[cx_enums#01](../cppcx/codesnippet/CPP/cpp/class1.h#01)]  
  
 L'exemple suivant montre comment le consommer :  
  
 [!code-cpp[cx_enums#02](../cppcx/codesnippet/CPP/cpp/class1.h#02)]  
  
### <a name="examples"></a>Exemples  
 Les exemples suivants indiquent comment déclarer un enum,  
  
 [!code-cpp[cx_enums#03](../cppcx/codesnippet/CPP/cpp/class1.h#03)]  
  
 L'exemple suivant indique comment effectuer un cast en équivalents numériques et effectuer des comparaisons. Notez que l'utilisation de l'énumérateur `One` est limitée par l'identificateur d'énumération `Enum1` et que l'énumérateur `First` est limité par `Enum2`.  
  
 [!code-cpp[cx_enums#04](../cppcx/codesnippet/CPP/cpp/class1.h#04)]  
  
## <a name="see-also"></a>Voir aussi  
 [Système de type](../cppcx/type-system-c-cx.md)   
 [Référence du langage Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Référence des espaces de noms](../cppcx/namespaces-reference-c-cx.md)