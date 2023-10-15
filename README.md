# Ansible Practical Work

### Финальный практикум по курсу Ansible

**Задание**: Необходимо подготовить сервер для работы приложения на основе ОС Centos 7

**Выполнено**:
- подготовлена вспомогательная роль `pgsql_xpaste` для развертывания PostgreSQL сервера;
- подготовлена основная роль `xpaste`, достаточная для запуска одиночного самостоятельного сервера **Xpaste**;
- созданы сценарии для `Molecule`, позволяющие автоматически тестировать обе роли;
- написана документация для обеих ролей:
  * [pgsql_xpaste](roles/pgsql_xpaste/README.md)
  * [xpaste](roles/xpaste/README.md)
- использован стек технологий, представленных в курсе:
  * Git
  * Vagrant/Virtualbox
  * Ansible
    * Core
    * Jinja
    * Playbooks
    * Roles
    * Galaxy
    * Vault
    * Linter
  * Molecule
