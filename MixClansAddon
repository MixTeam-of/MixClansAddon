<?php
declare(strict_types=1);

/**
 * @name MixClansAddon
 * @version 0.0.1-BETA
 * @main JackMD\ScoreHud\Addons\MixClansAddon
 * @depend MixClansUI
 */
namespace JackMD\ScoreHud\Addons {

    use JackMD\ScoreHud\addon\AddonBase;
    use pocketmine\Player;
    use MixTeam\Clans\Main;

    class MixClansAddon extends AddonBase
    {
        /** @var Main */
        private $MixClansUI;

        public function onEnable(): void
        {
            $this->MixClansUI = $this->getServer()->getPluginManager()->getPlugin("MixClansUI");
        }

        /**
         * @param Player $player
         * @return array
         */
        public function getProcessedTags(Player $player): array
        {
            return [
                "{clan_name}" => $this->getPlayerClan($player),
                "{clan_rank}" => $this->getPlayerClanRank($player),
                "{clan_members}" => $this->getPlayerClanMembers($player)
            ];
        }

        /**
         * @param Player $player
         * @return string
         */
        public function getPlayerClan(Player $player): string
        {
            $player = $this->MixClansUI->getPlayer($player);
            if ($player->isInClan()) {
                return $player->getClan()->getName();
            } else {
                return "/";
            }
        }

        /**
         * @param Player $player
         * @return string
         */
        public function getPlayerClanRank(Player $player)
        {
            $player = $this->MixClansUI->getPlayer($player);
            if ($player->isInClan()) {
                return $player->getClan()->getRank($player->getPlayer());
            } else {
                return "/";
            }
        }

        /**
         * @param Player $player
         * @return string
         */
        public function getPlayerClanMembers(Player $player)
        {
            $player = $this->MixClansUI->getPlayer($player);
            if ($player->isInClan()) {
                return (string)count($player->getClan()->getMembers());
            } else {
                return "/";
            }
        }

    }
}
