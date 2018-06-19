---
title: Représentation à virgule flottante IEEE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- float keyword
- real*8 value
- floating-point numbers, IEEE representation
- double data type, floating-point representation
- IEEE floating point representation
- real*10 value
- long double
- real*4 value
ms.assetid: 537833e8-fe05-49fc-8169-55fd0314b195
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d209d1c2a7429515383f8ebe80c621d6f2b15890
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379430"
---
# <a name="ieee-floating-point-representation"></a>Représentation à virgule flottante IEEE
Microsoft Visual C++ est compatible avec les standards numériques IEEE. Il existe trois variétés de nombres réels. Real\*4 et réel\*8 sont utilisés dans Visual C++. Real\*4 est déclaré à l’aide du mot **float**. Real\*8 est déclaré à l’aide du mot **double**. Dans la programmation de Windows 32 bits, le `long double` est mappé au type de données **double**. Il est toutefois prise en charge du langage d’assembly pour effectuer des calculs à l’aide du véritable * type de données de 10.  
  
 Les valeurs sont stockées comme suit :  
  
|Value|Stockées en tant que|  
|-----------|---------------|  
|réel * 4|bit de signe, exposant 8 bits, mantisse 23 bits|  
|réel * 8|bit de signe, exposant de 11 bits, mantisse 52 bits|  
|réel * 10|bit de signe, exposant de 15 bits, 64 bits de mantisse|  
  
 Dans réel * 4 et réel\*8 formats, il existe une valeur 1 dans la mantisse qui n’est pas stockée dans la mémoire, afin des mantisses correspondent en fait à 24 ou 53 bits, même si seuls 23 ou 52 bits sont stockés. Réel\*format 10 stocke réellement ce bit.  
  
 Les exposants sont tronqués de la moitié de leur valeur possible. Cela signifie que vous soustrayez cet écart de l’exposant stocké pour obtenir l’exposant réel. Si l’exposant stocké est inférieur à l’écart, il est en fait un exposant négatif.  
  
 Les exposants sont tronqués comme suit :  
  
|Exposant|Influencé par|  
|--------------|---------------|  
|8 bits (réel * 4)|127|  
|11 bits (réel * 8)|1023|  
|15 bits (réel * 10)|16383|  
  
 Ces exposants ne sont pas des puissances de dix ; ils sont des puissances de deux. Autrement dit, les exposants 8 bits stockés peuvent être jusqu'à 127. La valeur 2 ** 127 est à peu près équivalente à 10\*\*38, qui est la limite effective de réel\*4.  
  
 La mantisse est stockée sous forme de fraction binaire au format format 1.XXX.... Cette fraction a une valeur supérieure ou égale à 1 et inférieur à 2. Notez que les nombres réels sont toujours stockés sous forme normalisée ; Autrement dit, la mantisse est décalée vers la gauche telles que le bit de poids fort de la mantisse est toujours 1. Étant donné que ce bit est toujours 1, il est implicite (non stocké) dans le réel * 4 et réel\*8 formats. La virgule binaire (non décimale) est censée pour être situé à droite de la valeur 1.  
  
 Le format, puis, pour les différentes tailles est comme suit :  
  
|Format|OCTET 1|OCTET 2|OCTET 3|OCTETS 4|...|OCTET n|  
|------------|------------|------------|------------|------------|---------|------------|  
|réel * 4|`SXXX XXXX`|`XMMM MMMM`|`MMMM MMMM`|`MMMM MMMM`|||  
|réel * 8|`SXXX XXXX`|`XXXX MMMM`|`MMMM MMMM`|`MMMM MMMM`|...|`MMMM MMMM`|  
|réel * 10|`SXXX XXXX`|`XXXX XXXX`|`1MMM MMMM`|`MMMM MMMM`|...|`MMMM MMMM`|  
  
 `S` représente le bit de signe, le `X`de sont des bits de l’exposant et la `M`de sont des bits de la mantisse. Notez que le bit de gauche est supposé dans réel * 4 et réel\*8 met en forme, mais est présent en tant que « 1 » dans les 3 octets de la valeur réelle\*format 10.  
  
 Pour décaler la virgule binaire correctement, vous pouvez tout d’abord devez l’exposant et ensuite déplacer la virgule binaire vers la droite ou gauche du nombre approprié de bits.  
  
## <a name="examples"></a>Exemples  
 Voici quelques exemples de réel * 4 format :  
  
-   Dans l’exemple suivant, le bit de signe est zéro et l’exposant stocké est 128, ou 100 0000 0 en notation binaire, soit 127 plus 1. La mantisse stockée est (1). 000 0000 ... 0000 0000, qui a un implicite 1 et binaire point principal, la mantisse réelle est une.  
  
    ```  
                        SXXX XXXX XMMM MMMM ... MMMM MMMM  
    2   =  1  * 2**1  = 0100 0000 0000 0000 ... 0000 0000 = 4000 0000  
    ```  
  
-   Identique à l’option + 2 sauf que le bit de signe est défini. Cela est vrai pour tous les nombres à virgule flottante de format IEEE.  
  
    ```  
    -2  = -1  * 2**1  = 1100 0000 0000 0000 ... 0000 0000 = C000 0000  
    ```  
  
-   Même mantisse, exposant augmente de 1 (valeur biaisée est 129, soit 100 0000 1 en binaire.  
  
    ```  
    4  =  1  * 2**2  = 0100 0000 1000 0000 ... 0000 0000 = 4080 0000  
    ```  
  
-   Même exposant, la mantisse est supérieure de moitié — il (1). 100 0000... 0000 0000, c'est-à-dire, car il s’agit d’une fraction binaire, 1 1/2 (les valeurs des nombres fractionnaires sont 1/2, 1/4, 1/8 et ainsi de suite).  
  
    ```  
    6  = 1.5 * 2**2  = 0100 0000 1100 0000 ... 0000 0000 = 40C0 0000  
    ```  
  
-   Même exposant que d’autres puissances de deux, la mantisse est une inférieur à deux 127, soit 011 1111 1 en binaire.  
  
    ```  
    1  = 1   * 2**0  = 0011 1111 1000 0000 ... 0000 0000 = 3F80 0000  
    ```  
  
-   L’exposant tronqué équivaut à 126, 011 1111 0 en représentation binaire et la mantisse est (1). 100 0000 ... 0000 0000, 1 1/2.  
  
    ```  
    .75 = 1.5 * 2**-1 = 0011 1111 0100 0000 ... 0000 0000 = 3F40 0000  
    ```  
  
-   Exactement identique à deux sauf que le bit qui représente 1/4 est défini dans la mantisse.  
  
    ```  
    2.5 = 1.25 * 2**1 = 0100 0000 0010 0000 ... 0000 0000 = 4020 0000  
    ```  
  
-   1/10 est une fraction itérative en binaire. La mantisse est juste en deçà de 1.6, et l’exposant tronqué indique que 1.6 doit être divisée par 16 (il est 011 1101 1 en binaire, soit 123 au format décimal). L’exposant réel est 123-127 = - 4, ce qui signifie que le facteur par lequel multiplier est 2 ** -4 = 1/16. Notez que la mantisse stockée est arrondie dans le dernier bit — une tentative pour représenter le nombre non représentable aussi précisément que possible. (La raison pour laquelle ce 1/10 et 1 100 sont pas exactement représentable dans le fichier binaire est similaire à la raison que 1/3 est représentable pas exactement au format décimal.)  
  
    ```  
    0.1 = 1.6 * 2**-4 = 0011 1101 1100 1100 ... 1100 1101 = 3DCC CCCD  
    ```  
  
-   `0  = 1.0 * 2**-128 = all zeros--a special case.`  
  
## <a name="see-also"></a>Voir aussi  
 [Pourquoi les nombres à virgule flottante peuvent manquer de précision](../../build/reference/why-floating-point-numbers-may-lose-precision.md)