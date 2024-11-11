package registrarcontato

import (
	"database/sql"
	"fmt"

	_ "github.com/go-sql-driver/mysql"
)

func inserircontato(nome string, sobrenome string, apelido string, numero int64, email string) error {
	// String de conexão com o banco MySQL
	dsn := "root:Oracle6i2020@tcp(agenda.c9oow0ewet8p.us-east-2.rds.amazonaws.com:3306)/dbagenda"

	//Abrir conexão com o banco
	db, err := sql.Open("mysql", dsn)
	if err != nil {
		return fmt.Errorf("erro ao conectar ao banco de dados: %v", err)
	}
	defer db.Close()

	//Valida a conexão
	if err := db.Ping(); err != nil {
		return fmt.Errorf("Erro ao validar se conectou ao banco")
	}

	//Query
	query := `INSERT INTO contatos (idcontatos, nome, sobrenome, apelido, numero, email, data_criacao, data_alteracao) 
			  VALUES (?, ?, ?, ?, ?, ?, ?, ?)`

	//variaveis valores fixos
	idagenda := ""
	dataagora := "SYSDATE()"

	//Comando de inserção
	_, err = db.Exec(query, idagenda, nome, sobrenome, apelido, numero, email, dataagora, dataagora)
	if err != nil {
		return fmt.Errorf("Erro ao executar o insert: %v", err)
	}

	return nil
}

/*
func main() {
	err := inserircontato("Teste", "código", "Testando", 123456789, "teste@gmail.com")
	if err != nil {
		log.Fatalf("Erro: %v", err)
	} else {
		fmt.Println("Registro inserido com sucesso!")
	}
}
*/
