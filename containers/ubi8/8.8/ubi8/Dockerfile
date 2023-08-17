FROM registry.access.redhat.com/ubi8:8.8@sha256:8fea2399f44a9dfdfa18eec4e3e5d2e1d71f0a865dd1d5c66215a6d68ccafa8a

LABEL org.opencontainers.image.created="2023-08-14T21:01:50Z" \
      org.opencontainers.image.title: "ubi8"
      org.opencontainers.image.description: "Red Hat Universal Base Images (UBI) are OCI-compliant container base operating system images with complementary runtime languages and packages that are freely redistributable."
      org.opencontainers.image.licenses: "Red Hat Universal Base Image EULA"
      org.opencontainers.image.url: "https://catalog.redhat.com/software/container-stacks/detail/5ec53f50ef29fd35586d9a56"
      org.opencontainers.image.vendor: "Redhat"
      org.opencontainers.image.version: "8.8"

COPY rootfs /

RUN sed -i "s/enabled=1/enabled=0/" /etc/dnf/plugins/subscription-manager.conf && \
    echo "exclude=filesystem-*" >> /etc/dnf/dnf.conf && \
    chmod 644 /etc/issue && \
    chmod +x /usr/local/src/hardening/*.sh && \
    dnf repolist && \
    dnf update -y --exclude=redhat-release && \
    dnf install -y cracklib-dicts nss && \
    echo "* hard maxlogins 10" > /etc/security/limits.d/maxlogins.conf && \
    /hardening/xccdf_org.ssgproject.content_rule_account_disable_post_pw_expiration.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_logon_fail_delay.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_max_concurrent_login_sessions.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_maximum_age_login_defs.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_minimum_age_login_defs.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_password_minlen_login_defs.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_password_pam_dcredit.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_password_pam_dictcheck.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_password_pam_difok.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_password_pam_lcredit.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_password_pam_maxclassrepeat.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_password_pam_maxrepeat.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_password_pam_minclass.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_password_pam_minlen.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_password_pam_ocredit.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_password_pam_pwhistory_remember_password_auth.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_password_pam_pwhistory_remember_system_auth.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_password_pam_ucredit.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_password_pam_unix_remember.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_passwords_pam_faillock_deny.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_passwords_pam_faillock_deny_root.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_passwords_pam_faillock_interval.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_passwords_pam_faillock_unlock_time.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_passwords_pam_faillock.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_umask_etc_bashrc.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_umask_etc_csh_cshrc.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_umask_etc_login_defs.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_accounts_umask_etc_profile.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_banner_etc_issue.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_package_crypto-policies_installed.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_configure_crypto_policy.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_configure_kerberos_crypto_policy.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_configure_openssl_crypto_policy.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_configure_gnutls_tls_crypto_policy.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_harden_sshd_ciphers_openssh_conf_crypto_policy.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_harden_sshd_ciphers_opensshserver_conf_crypto_policy.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_harden_sshd_macs_openssh_conf_crypto_policy.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_harden_sshd_macs_opensshserver_conf_crypto_policy.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_coredump_disable_backtraces.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_coredump_disable_storage.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_disable_ctrlaltdel_burstaction.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_disable_users_coredumps.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_display_login_attempts.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_ensure_gpgcheck_local_packages.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_file_groupownership_system_commands_dirs.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_network_configure_name_resolution.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_no_empty_passwords.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_openssl_use_strong_entropy.sh && \
    /hardening/xccdf_org.ssgproject.content_rule_package_iptables_installed.sh && \
    chmod +t /tmp /var/tmp && \
    dnf remove -y vim-minimal && \
    dnf clean all && \
    rm -rf /usr/local/src/hardening/ /var/cache/dnf/ /var/tmp/* /tmp/* /var/tmp/.???* /tmp/.???*

RUN set -eux; \
    disabledAlgorithms=' \
       TLS_CHACHA20_POLY1305_SHA256, \
       TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305_SHA256, \
       TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256, \
       TLS_DHE_RSA_WITH_CHACHA20_POLY1305_SHA256, \
    '; \
    disabledAlgorithms="${disabledAlgorithms//[[:space:]]/}"; \
    sed -i "s/^jdk\.tls\.disabledAlgorithms=/jdk.tls.disabledAlgorithms=$disabledAlgorithms/" \
       /usr/share/crypto-policies/FIPS/java.txt;

ENV container oci
ENV PATH /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

CMD ["/bin/bash"]