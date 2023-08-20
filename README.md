# tabelas_bancoDados



### Tabela Paciente


          CREATE TABLE `paciente` (
              `codigoconvenio` int(11) NOT NULL,
              `numeropaciente` int(11) NOT NULL,
              `nome` varchar(50) NOT NULL
          );

          ALTER TABLE `paciente`
              ADD PRIMARY KEY (`codigoconvenio`,`numeropaciente`);

          ALTER TABLE `paciente`
            ADD CONSTRAINT `FK-convenio` FOREIGN KEY (`codigoconvenio`) REFERENCES `convenio` (`codigoconvenio`);
          COMMIT;
  
          INSERT INTO `paciente` (`codigoconvenio`, `numeropaciente`, `nome`) VALUES
            (1, 1, 'Luke Skywalker'),
            (2, 10, 'Obi Wan Kenobi'),
            (3, 1, 'Jeige Romans'),
            (3, 2, 'Elma Maria'),
            (4, 1, 'Paula da Luz');


### Tabela Médico


          CREATE TABLE `medico` (
              `crm` int(11) NOT NULL,
              `nome` varchar(50) NOT NULL,
              `especializacao` varchar(50) NOT NULL
          );



          ALTER TABLE `medico`
            ADD PRIMARY KEY (`crm`);
          COMMIT;


          INSERT INTO `medico` (`crm`, `nome`, `especializacao`) VALUES
          (1, 'Adamastor Castor', 'Ginecologista'),
          (2, 'Gertrudes Cruzes', 'Cardiologista'),
          (3, 'Trophozilda Silva', 'Oncologista'),
          (4, 'Matusalem Montanha', 'Cardiologista'),
          (5, 'Darth Vader', 'Urologista');

### Tabela Convenio

        CREATE TABLE `convenio` (
            `codigoconvenio` int(11) NOT NULL,
            `nome` varchar(50) NOT NULL
        );


        ALTER TABLE `convenio`
          ADD PRIMARY KEY (`codigoconvenio`);
        COMMIT;


        INSERT INTO `convenio` (`codigoconvenio`, `nome`) VALUES
        (1, 'Samaritano'),
        (2, 'UNIMED'),
        (3, 'Amil'),
        (4, 'Beneficência Portuguesa'),
        (5, 'Vera Cruz');
           

### Tabela Consulta
	
    	CREATE TABLE `consulta` (
            `codigoconvenio` int(11) NOT NULL,
            `numeropaciente` int(11) NOT NULL,
            `crm` int(11) NOT NULL,
            `diahoraconsulta` date NOT NULL
           
      );


        ALTER TABLE `consulta`
          ADD PRIMARY KEY (`codigoconvenio`,`numeropaciente`,`crm`,`diahoraconsulta`),
          ADD KEY `FK-medico` (`crm`);


        ALTER TABLE `consulta`
          ADD CONSTRAINT `FK-consultaconvenio` FOREIGN KEY (`codigoconvenio`) REFERENCES `convenio` (`codigoconvenio`),
          ADD CONSTRAINT `FK-medico` FOREIGN KEY (`crm`) REFERENCES `medico` (`crm`),
          ADD CONSTRAINT `FK-paciente` FOREIGN KEY (`codigoconvenio`,`numeropaciente`) REFERENCES `paciente` (`codigoconvenio`, `numeropaciente`);
        COMMIT;
  
        INSERT INTO `consulta` (`codigoconvenio`, `numeropaciente`, `crm`, `diahoraconsulta`) VALUES
          (3, 2, 4, '2023-05-09'),
          (4, 1, 5, '2023-05-23');

  
