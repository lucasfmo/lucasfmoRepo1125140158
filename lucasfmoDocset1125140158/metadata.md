<properties
    pageTitle="Driver property doesn't correspond to an installed ODBC driver"
    description="A propriedade "Controlador" não corresponde a um controlador ODBC instalado"
    service="microsoft.analysisservices"
    resource="servers"
    authors="bnmaa"
    displayOrder="2"
    selfHelpType="resource"
    supportTopicIds=""
    resourceTags=""
    productPesIds=""
    cloudEnvironments="MoonCake"
/>

# <a name="driver-property-doesnt-correspond-to-an-installed-odbc-driver"></a>A propriedade "Controlador" não corresponde a um controlador ODBC instalado

## <a name="recommended-steps"></a>**Passos recomendados**

1. Abra o cmd.exe elevado (executar como administrador) e execute **%windir%\system32\odbcad32.exe**, para abrir o Administrador de Origem de Dados de ODBC de 64 bits.
2. Aceda ao separador **Controladores**, certifique-se de que o controlador ODBC pretendido aparece.
3. Caso contrário, instale o controlador ODBC de 64 bits corretamente.
4. Reinicie o serviço de gateway.

## <a name="recommended-documents"></a>**Documentos recomendados**

[Administrador de Origem de Dados de ODBC](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator) <br />
[Ver controladores de ODBC](https://docs.microsoft.com/sql/odbc/admin/viewing-drivers)
