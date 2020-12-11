---
description: 'En savoir plus sur : source de données : configuration d’une source de données ODBC par programmation'
title: "Source de données : configuration d'une source de données ODBC par programme"
ms.date: 11/04/2016
f1_keywords:
- SQLConfigDataSource
helpviewer_keywords:
- ODBC data sources, configuring
- SQLConfigDataSource method example
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: b8cabe9b-9e12-4d73-ae36-7cb12dee3213
ms.openlocfilehash: 4d3cab3de1a3b65bd8df9aee2b91bbaf243926d6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155720"
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>Source de données : configuration d'une source de données ODBC par programme

Cette rubrique explique comment configurer des noms de sources de données Open Database Connectivity (ODBC) par programmation. Vous bénéficiez ainsi d’une certaine flexibilité pour accéder aux données sans forcer l’utilisateur à utiliser explicitement l’administrateur ODBC ou d’autres programmes pour spécifier les noms des sources de données.

En règle générale, un utilisateur exécute l’administrateur ODBC pour créer une source de données si le système de gestion de base de données (SGBD) associé prend en charge cette opération.

Lors de la création d’une source de données ODBC Microsoft Access par le biais de l’administrateur ODBC, vous avez le choix entre deux options : vous pouvez sélectionner un fichier. mdb existant ou créer un nouveau fichier. mdb. Il n’existe aucun moyen de créer le fichier. mdb par programmation à partir de votre application ODBC MFC. Par conséquent, si votre application nécessite de placer des données dans une source de données Microsoft Access (fichier. mdb), vous souhaiterez probablement disposer d’un fichier. mdb vide que vous pouvez utiliser ou copier chaque fois que vous en avez besoin.

Toutefois, de nombreux SGBD autorisent la création de sources de données par programmation. Certaines sources de données conservent une spécification de répertoire pour les bases de données. Autrement dit, un répertoire est la source de données et chaque table de la source de données est stockée dans un fichier séparé (dans le cas de dBASE, chaque table est un fichier. dbf). Les pilotes d’autres bases de données ODBC, tels que Microsoft Access et SQL Server, requièrent que certains critères spécifiques soient respectés pour qu’une source de données puisse être établie. Par exemple, lors de l’utilisation du pilote ODBC SQL Server, vous devez avoir établi un ordinateur SQL Server.

## <a name="sqlconfigdatasource-example"></a><a name="_core_sqlconfigdatasource_example"></a> Exemple de SQLConfigDataSource

L’exemple suivant utilise la `::SQLConfigDataSource` fonction API ODBC pour créer une source de données Excel nommée New Excel Data Source :

```
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",
                   "DSN=New Excel Data Source\0"
                   "Description=New Excel Data Source\0"
                   "FileType=Excel\0"
                   "DataDirectory=C:\\EXCELDIR\0"
                   "MaxScanRows=20\0");
```

Notez que la source de données est en fait un répertoire (C:\EXCELDIR); ce répertoire doit exister. Le pilote Excel utilise des répertoires comme sources de données et fichiers en tant que tables individuelles (une table par fichier. xls).

Pour plus d’informations sur la création de tables, consultez [source de données : création d’une table par programmation dans une source de données ODBC](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md).

Les informations suivantes décrivent les paramètres qui doivent être passés à la `::SQLConfigDataSource` fonction API ODBC. Pour utiliser `::SQLConfigDataSource` , vous devez inclure le fichier d’en-tête Odbcinst. h et utiliser la bibliothèque d’importation Odbcinst. lib. En outre, Odbccp32.dll doit se trouver dans le chemin d’accès au moment de l’exécution (ou Odbcinst.dll pour 16 bits).

Vous pouvez créer un nom de source de données ODBC à l’aide de l’administrateur ODBC ou d’un utilitaire similaire. Toutefois, il est parfois souhaitable de créer un nom de source de données directement à partir de votre application pour obtenir l’accès sans que l’utilisateur n’ait à exécuter un utilitaire séparé.

L’administrateur ODBC (généralement installé dans le panneau de configuration) crée une source de données en plaçant des entrées dans le Registre Windows (ou, pour les 16 bits, dans le fichier Odbc.ini). Le gestionnaire de pilotes ODBC interroge ce fichier pour obtenir les informations nécessaires sur la source de données. Il est important de connaître les informations qui doivent être placées dans le registre, car vous devez les fournir avec l’appel à `::SQLConfigDataSource` .

Bien que ces informations puissent être écrites directement dans le registre sans utiliser `::SQLConfigDataSource` , toute application qui le fait repose sur la technique actuelle utilisée par le gestionnaire de pilotes pour conserver ses données. Si une révision ultérieure du gestionnaire de pilotes ODBC implémente la conservation des enregistrements sur les sources de données d’une manière différente, toute application qui utilise cette technique est interrompue. Il est généralement recommandé d’utiliser une fonction API lorsqu’une fonction est fournie. Par exemple, votre code est portable de 16 bits à 32 bits si vous utilisez la `::SQLConfigDataSource` fonction, car la fonction écrit correctement dans le fichier Odbc.ini ou dans le registre.

## <a name="sqlconfigdatasource-parameters"></a><a name="_core_sqlconfigdatasource_parameters"></a> Paramètres de SQLConfigDataSource

La rubrique suivante décrit les paramètres de la `::SQLConfigDataSource` fonction. La plupart des informations proviennent de la *Référence du programmeur* de l’API ODBC fournie avec Visual C++ version 1,5 et versions ultérieures.

### <a name="function-prototype"></a><a name="_core_function_prototype"></a> Prototype de fonction

```
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);
```

### <a name="remarks"></a>Notes

#### <a name="parameters-and-usage"></a><a name="_core_parameters_and_usage"></a> Paramètres et utilisation

*hwndParent*<br/>
Fenêtre spécifiée en tant que propriétaire de toutes les boîtes de dialogue que le gestionnaire de pilotes ODBC ou le pilote ODBC crée pour obtenir des informations supplémentaires de la part de l’utilisateur sur la nouvelle source de données. Si le paramètre *lpszAttributes* ne fournit pas suffisamment d’informations, une boîte de dialogue s’affiche. Le paramètre *hwndParent* peut avoir la valeur null.

*lpszDriver*<br/>
Description du pilote. Il s’agit du nom présenté aux utilisateurs plutôt que du nom du pilote physique (la DLL).

*lpszAttributes*<br/>
Liste d’attributs sous la forme « KeyName = value ». Ces chaînes sont séparées par des marques de fin null avec deux marques de fin null consécutives à la fin de la liste. Ces attributs sont principalement des entrées propres au pilote par défaut, qui entrent dans le registre pour la nouvelle source de données. Une clé importante qui n’est pas mentionnée dans la référence de l’API ODBC pour cette fonction est « DSN » (« Data Source Name »), qui spécifie le nom de la nouvelle source de données. Le reste des entrées est spécifique au pilote pour la nouvelle source de données. Il n’est souvent pas nécessaire de fournir toutes les entrées, car le pilote peut demander à l’utilisateur des boîtes de dialogue pour les nouvelles valeurs. (Affectez à *hwndParent* la valeur null pour l’entraîner). Vous pouvez fournir explicitement des valeurs par défaut afin que l’utilisateur ne soit pas invité à le faire.

#### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>Pour déterminer la description d’un pilote pour le paramètre lpszDriver à l’aide de l’administrateur ODBC

1. Exécutez l’administrateur ODBC.

1. Cliquez sur **Add**.

Vous obtenez ainsi une liste des pilotes installés et leurs descriptions. Utilisez cette description comme paramètre *lpszDriver* . Notez que vous utilisez la description complète, telle que « fichiers Excel (*. xls) », y compris l’extension de nom de fichier et les parenthèses si elles existent dans la description.

Vous pouvez également examiner le registre (ou, pour les 16 bits, le fichier Odbcinst.ini), qui contient une liste de toutes les entrées et descriptions de pilote sous la clé de Registre « pilotes ODBC » (ou la section [pilotes ODBC] dans Odbcinst.ini).

L’une des façons de trouver les KeyNames et les valeurs pour le paramètre *lpszAttributes* consiste à examiner le fichier Odbc.ini pour une source de données déjà configurée (peut-être une source de données qui a été configurée par l’administrateur ODBC).

#### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>Pour rechercher les noms et les valeurs du paramètre lpszAttributes

1. Exécutez l’éditeur du Registre Windows (ou, pour les 16 bits, ouvrez le fichier Odbc.ini).

1. Recherchez les informations relatives aux sources de données ODBC à l’aide d’un des éléments suivants :

   - Pour 32 bits, recherchez la clé **HKEY_CURRENT_USER\Software\ODBC\ODBC.INI sources de données \ODBC** dans le volet gauche.

      Le volet droit répertorie les entrées de la forme : « pub : REG_SZ : *\<data source name>* », où *\<data source name>* est une source de données qui a déjà été configurée avec les paramètres souhaités pour le pilote que vous prévoyez d’utiliser. Sélectionnez la source de données souhaitée, par exemple SQL Server. Les éléments qui suivent la chaîne « pub : » sont, dans l’ordre, le KeyName et la valeur à utiliser dans votre paramètre *lpszAttributes* .

   - Pour 16 bits, recherchez la section dans le fichier Odbc.ini marqué par [ *\<data source name>* ].

      Les lignes qui suivent cette ligne se présentent sous la forme « KeyName = value ». Il s’agit exactement des entrées à utiliser dans votre paramètre *lpszAttributes* .

Vous pouvez également examiner la documentation du pilote spécifique que vous allez utiliser. Vous trouverez des informations utiles dans l’aide en ligne du pilote, à laquelle vous pouvez accéder en exécutant l’administrateur ODBC. Ces fichiers d’aide sont généralement placés dans le répertoire WINDOWS\SYSTEM pour Windows NT, Windows 3,1 ou Windows 95.

#### <a name="to-obtain-online-help-for-your-odbc-driver"></a>Pour obtenir de l’aide en ligne pour votre pilote ODBC

1. Exécutez l’administrateur ODBC.

1. Cliquez sur **Add**.

1. Sélectionnez le nom du pilote.

1. Cliquez sur **OK**.

Lorsque l’administrateur ODBC affiche les informations relatives à la création d’une nouvelle source de données pour ce pilote particulier, cliquez sur **aide**. Cela ouvre le fichier d’aide de ce pilote particulier, qui contient généralement des informations importantes concernant l’utilisation du pilote.

## <a name="see-also"></a>Voir aussi

[Source de données (ODBC)](../../data/odbc/data-source-odbc.md)
